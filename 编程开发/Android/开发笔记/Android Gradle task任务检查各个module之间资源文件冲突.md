做组件化开发的时候，我们经常会遇到各个不同的module之间资源文件冲突的问题，运行也不报错，但是会出现覆盖的问题，导致运行之后发送错误的效果。

所以我们需要利用一个gradlke 脚本task，来自动化检查资源文件冲突。

定义一个android gradle脚本，检查各个module之间资源文件冲突（命令重复）的task。



  [Android基于gradle task检查各个module之间资源文件冲突情况](https://developer.aliyun.com/article/1622652?source=5176.11533457&userCode=ywqc0ubl) 

  [Android不同module资源布局文件重名被覆盖](https://developer.aliyun.com/article/1621283?source=5176.11533457&userCode=ywqc0ubl)



下面是一个完整的 Gradle 脚本示例，用于检查不同模块之间的资源文件冲突。这个任务将遍历所有子模块的资源文件，并在发现同名文件时输出冲突信息。脚本中包含了详细的注释，便于理解每个步骤。

### 1. 根 `build.gradle` 文件

在项目的根目录下的 `build.gradle` 文件中定义任务：

```c
groovy复制代码// 根 build.gradle 文件
buildscript {
    repositories {
        google()
        mavenCentral()
    }
    dependencies {
        classpath 'com.android.tools.build:gradle:8.1.1' // 请根据需要调整版本
    }
}

allprojects {
    repositories {
        google()
        mavenCentral()
    }
}

task checkResourceConflicts {
    doLast {
        def resourceFiles = [:] // 存储资源文件，键是文件名，值是包含文件路径和模块名的 Map

        // 遍历所有子模块
        subprojects { subproject ->
            // 检查子模块是否有 Android 配置
            if (subproject.hasProperty('android')) {
                subproject.android.sourceSets.each { sourceSet ->
                    sourceSet.res.srcDirs.each { resDir ->
                        if (resDir.exists()) {
                            println("Scanning resources in module: ${subproject.name}, path: ${resDir.absolutePath}")

                            // 遍历资源目录中的文件
                            resDir.eachFileRecurse { file ->
                                if (file.isFile() && file.name.endsWith(".xml")) {
                                    def fileName = file.name
                                    def moduleName = subproject.name // 当前模块名

                                    // 检查文件名是否已存在
                                    if (resourceFiles.containsKey(fileName)) {
                                        def existingFileInfo = resourceFiles[fileName]
                                        if (existingFileInfo.moduleName != moduleName) {
                                            // 如果文件名来自不同模块，报告冲突
                                            println "Resource conflict detected: ${fileName} exists in both ${existingFileInfo.moduleName} (${existingFileInfo.filePath}) and ${moduleName} (${file.absolutePath})"
                                        }
                                    } else {
                                        // 存储文件路径及模块名
                                        resourceFiles[fileName] = [filePath: file.absolutePath, moduleName: moduleName]
                                    }
                                }
                            }
                        } else {
                            println("No resources found in: ${resDir.absolutePath}")
                        }
                    }
                }
            } else {
                println("Skipping module: ${subproject.name} (no Android configuration)")
            }
        }

        println("Resource conflict check completed.")
    }
}

// 在构建之前执行检查任务
gradle.projectsEvaluated {
    tasks.named("preBuild").configure {
        dependsOn(checkResourceConflicts)
    }
}
```

### 2. 代码说明

- **任务 `checkResourceConflicts`**：
  - 遍历所有子模块，检查每个模块的资源文件。
  - 使用 `subprojects` 来遍历每个子模块。
  - 检查每个模块是否包含 `android` 配置。
  - 如果存在资源文件，逐一检查是否有同名文件。
  - 如果检测到同名文件，输出冲突信息，包含模块名和文件路径。
- **`preBuild` 任务的依赖**：
  - 在所有项目评估完成后，将 `checkResourceConflicts` 任务与 `preBuild` 任务关联，这样每次构建都会执行检查。



### 3. 使用步骤

1. **在项目根目录的 `build.gradle` 文件中添加以上代码**。

2. **确保 `settings.gradle` 文件中包含所有子模块**，例如：

   

   ```java
   groovy
   
   
   复制代码
   include ':app', ':module1', ':module2'
   ```

3. **运行构建命令**：

   

   ```javascript
   bash
   
   
   复制代码
   ./gradlew assembleDebug
   ```

   

   该命令将触发资源冲突检查，并在控制台打印出任何资源文件冲突的信息。



### 4. 输出效果



当执行构建命令后，控制台将输出类似于以下的内容：



```java
bash复制代码Scanning resources in module: module1, path: /path/to/project/module1/src/main/res
Scanning resources in module: module2, path: /path/to/project/module2/src/main/res
Resource conflict detected: string_name.xml exists in both module1 (/path/to/project/module1/src/main/res/values/string_name.xml) and module2 (/path/to/project/module2/src/main/res/values/string_name.xml)
Resource conflict check completed.
```



这样就完成了一个有效的资源文件冲突检查任务。你可以根据需要进一步调整和优化该脚本。







**项目根目录gradle.build完整代码**：

```java
// Top-level build file where you can add configuration options common to all sub-projects/modules.
plugins {
    id 'com.android.application' version '8.6.0' apply false//8.6.0  '7.1.0
    id 'com.android.library' version '8.6.0' apply false//8.6.0   '7.1.0
    id 'maven-publish' apply true// 引入 maven 插件
    //引入kotlin 插件
    id 'org.jetbrains.kotlin.android' version '1.9.0' apply false
}

// 根 build.gradle
apply from: 'versions.gradle'

allprojects {
    // 在这里共享版本号给所有子项目
    ext {
        kotlinVersion = kotlinVersion
        appCompatVersion = appCompatVersion
        coroutinesVersion = coroutinesVersion
    }
}

task checkResourceConflicts {
    doLast {
        def resourceFiles = [:] // 存储资源文件，键是文件名，值是包含文件路径和模块名的 Map

        // 遍历所有子模块
        subprojects { subproject ->
            // 检查子模块是否有 Android 配置
            if (subproject.hasProperty('android')) {
                subproject.android.sourceSets.each { sourceSet ->
                    sourceSet.res.srcDirs.each { resDir ->
                        if (resDir.exists()) {
                            println("Scanning resources in [module]: [${subproject.name}], path: ${resDir.absolutePath}")

                            // 遍历资源目录中的文件
                            resDir.eachFileRecurse { file ->
                                if (file.isFile() && file.name.endsWith(".xml")) {
                                    def fileName = file.name
                                    def moduleName = subproject.name // 当前模块名

                                    // 检查文件名是否已存在
                                    if (resourceFiles.containsKey(fileName)) {
                                        def existingFileInfo = resourceFiles[fileName]
                                        if (existingFileInfo.moduleName != moduleName) {
                                            // 如果文件名来自不同模块，报告冲突
                                            println "Resource conflict detected: ${fileName} exists in both ${existingFileInfo.moduleName} (${existingFileInfo.filePath}) and ${moduleName} (${file.absolutePath})"
                                        }
                                    } else {
                                        // 存储文件路径及模块名
                                        resourceFiles[fileName] = [filePath: file.absolutePath, moduleName: moduleName]
                                    }
                                }
                            }
                        } else {
                          //  println("No resources found in: ${resDir.absolutePath}")
                        }
                    }
                }
            } else {
                println("Skipping module: ${subproject.name} (no Android configuration)")
            }
        }

        println("Resource conflict check completed.")
    }
}

// 在每个子模块的 preBuild 任务上执行检查
subprojects { subproject ->
    if (subproject.hasProperty('android')) {
        subproject.tasks.named("preBuild").configure {
            dependsOn(checkResourceConflicts)
        }
    }
}


```





 在项目根目录gradle.build文件中运行task：



![image-20241014150950342](https://s2.loli.net/2024/10/14/OMswiZNtknVRa4F.png)





**运行结果如图所示：**



```
> Task :checkResourceConflicts
Scanning resources in [module]: [app], path: D:\Projects\Android\widgets\app\src\aliyun\res
Scanning resources in [module]: [app], path: D:\Projects\Android\widgets\app\src\main\res
Scanning resources in [module]: [app], path: D:\Projects\Android\widgets\app\src\tuya\res
Scanning resources in [module]: [app], path: D:\Projects\Android\widgets\app\src\xiaomi\res
Scanning resources in [module]: [kotlinDemo], path: D:\Projects\Android\widgets\kotlinDemo\src\main\res
Resource conflict detected: activity_main.xml exists in both app (D:\Projects\Android\widgets\app\src\main\res\layout\activity_main.xml) and kotlinDemo (D:\Projects\Android\widgets\kotlinDemo\src\main\res\layout\activity_main.xml)
Resource conflict detected: strings.xml exists in both app (D:\Projects\Android\widgets\app\src\aliyun\res\values\strings.xml) and kotlinDemo (D:\Projects\Android\widgets\kotlinDemo\src\main\res\values\strings.xml)
Scanning resources in [module]: [widgets], path: D:\Projects\Android\widgets\widgets\src\main\res
Resource conflict detected: strings.xml exists in both app (D:\Projects\Android\widgets\app\src\aliyun\res\values\strings.xml) and widgets (D:\Projects\Android\widgets\widgets\src\main\res\values\strings.xml)
Resource conflict check completed.

Deprecated Gradle features were used in this build, making it incompatible with Gradle 9.0.

You can use '--warning-mode all' to show the individual deprecation warnings and determine if they come from your own scripts or plugins.

For more on this, please refer to https://docs.gradle.org/8.10.2/userguide/command_line_interface.html#sec:command_line_warnings in the Gradle documentation.
```



项目task运行结果如图所示：



![image-20241014151628307](https://s2.loli.net/2024/10/14/uarnjoZBmWsMp1H.png)