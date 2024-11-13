本系列学习教程笔记属于详细讲解Kotlin语法的教程，需要快速学习Kotlin语法的小伙伴可以查看“简洁” 系列的教程

**快速入门请阅读如下简洁教程：**
[Kotlin学习教程(一)](https://developer.aliyun.com/article/1618222?source=5176.11533457&userCode=ywqc0ubl)
[Kotlin学习教程(二)](https://developer.aliyun.com/article/1618225?source=5176.11533457&userCode=ywqc0ubl)
[Kotlin学习教程(三)](https://developer.aliyun.com/article/1618227?source=5176.11533457&userCode=ywqc0ubl)
[Kotlin学习教程(四)](https://developer.aliyun.com/article/1618229?source=5176.11533457&userCode=ywqc0ubl)
[Kotlin学习教程(五)](https://developer.aliyun.com/article/1618573?source=5176.11533457&userCode=ywqc0ubl)
[Kotlin学习教程(六)](https://developer.aliyun.com/article/1618575?source=5176.11533457&userCode=ywqc0ubl)
[Kotlin学习教程(七)](https://developer.aliyun.com/article/1618580?source=5176.11533457&userCode=ywqc0ubl)
[Kotlin学习教程(八)](https://developer.aliyun.com/article/1618834?source=5176.11533457&userCode=ywqc0ubl)
[Kotlin学习教程(九)](https://developer.aliyun.com/article/1618841?source=5176.11533457&userCode=ywqc0ubl)
[Kotlin学习教程(十)](https://developer.aliyun.com/article/1618844?source=5176.11533457&userCode=ywqc0ubl)

介绍
本次改造的项目地址为：github.com/stevenwsg/XSYBBS

这个项目是两年前在学校写的，当初写的时候比较赶时间，一直堆业务功能，没有考虑项目结构，写了很多重复代码。最近在看Kotlin协程和JetPack组件，就想着用Kotlin协程和JetPack组件对原项目进行重构。

**MVVM**
Android MVVM 架构图：


![image.png](https://ucc.alicdn.com/pic/developer-ecology/syv66y3m2ksnc_66945a0d0ceb45969de7805389c98b10.png)

各层介绍：

- Model层，主要负责数据的提供。Model层提供业务逻辑的数据结构（比如，实体类），提供数据的获取（比如，从本地数据库或者远程网络获取数据），提供数据的存储。
- View层，主要负责界面的显示。View层不涉及任何的业务逻辑处理，它持有ViewModel层的引用，当需要进行业务逻辑处理时通知ViewModel层。
- ViewModel层，主要负责业务逻辑的处理。ViewModel层不涉及任何的视图操作。ViewModel层中数据的变化可以自动通知View层进行更新，因此ViewModel层不需要持有View层的引用。

Google JetPack搭建MVVM：

![image.png](https://ucc.alicdn.com/pic/developer-ecology/syv66y3m2ksnc_4b99cc7b4fdb48fd9c86299825062325.png)
本次MVVM改造使用了JetPack的三个组件分别是：

-  Lifecycles
- ViewModel
- LiveData


Lifecycles

作用：更方便的处理Android中生命周期的问题，它可以使你的组件具有感知生命周期的能力，从而根据生命周期状态来自动的响应一些动作。

使用文档：https://developer.android.com/topic/libraries/architecture/lifecycle

ViewModel

作用： 用来管理数据，它同样具有感知生命周期的能力，在宿主没有被销毁之前，数据不会丢失，且ViewModel不会重新创建，比如旋转屏幕等。同时，ViewMedel将数据从Activity中抽离出去，耦合度更低，更加方便维护。

使用文档：https://developer.android.com/topic/libraries/architecture/viewmodel

LiveData

配合ViewModel一起使用，存在于ViewModel中

LiveData 是一个可观测数据的容器类，与普通的可观测类不同，LiveData 能感知生命周期，并且只会在这些可观测的应用组件处于活动状态的时候才会更新它们，而且还会在与其关联的生命周期被销毁后自动清理自己。这样一来也就不会出现内存泄漏的问题了。

作用：底层数据改变时会自动更新UI，实际上我们可以看做是ViewModel于View之间通信的桥梁

使用文档：https://developer.android.com/topic/libraries/architecture/livedata

改造用户反馈模块
在项目中添加 lifecycle-extensions 和 Kotlin 依赖

```js

    implementation 'androidx.lifecycle:lifecycle-extensions:2.2.0'
    implementation "androidx.core:core-ktx:1.2.0"
    implementation "androidx.lifecycle:lifecycle-viewmodel-ktx:2.2.0"
    implementation "org.jetbrains.kotlin:kotlin-stdlib-jdk7:$kotlin_version"

```

下面是项目的结构：

![image.png](https://ucc.alicdn.com/pic/developer-ecology/syv66y3m2ksnc_40f7b97228964ba4afe08f7cba7c0f06.png)




- bean 反馈实体和请求返回实体

- model 存放业务逻辑相关

- view 存放Activity

- viewmodel 存放viewmodel相关类


在MVVM中，通过LiveData来实现ViewModel与View层之间的通信的，而且这个通信不是手动的，其核心是通过数据驱动的，也就是数据发生变化，view层会感知到并自动刷新ui。

1、View
View 持有ViewModel 的引用，当需要和Model进行通信时，通过ViewModel来进行通信。同时监听ViewModel中的数据变化，当ViewModel中的数据改变时，刷新UI，实现数据驱动。

```js
class FeedBackActivity : BaseActivity() {

    private var mFeedBackVM : FeedBackViewModel? = null // 持有ViewModel的引用

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_feedback)
        initView()
        initVM()
        initObserval()
    }

    private fun initView() {
        bt_back.setOnClickListener {
            if (!TextUtils.isEmpty(et_back.text.toString())) {
                mFeedBackVM?.getFeedBackMessage(et_back.text.toString()) // 调用ViewModel 的反馈方法， 解耦，单一职责
            } else {
                Toasty.info(this@FeedBackActivity,  getString(R.string.text_tost_empty), Toast.LENGTH_SHORT, true).show()
            }

        }
    }

    private fun initVM() { // 初始化ViewModel
		mFeedBackVM = ViewModelProvider(this).get(FeedBackViewModel::class.java)
    }

    private fun initObserval() { // 观测数据，当ViewModel的LiveData数据改变时，更新UI
        mFeedBackVM?.messageLiveData?.observe(this, Observer { t ->
            if (t?.code == 0) {
                Toasty.success(this@FeedBackActivity, t.message, Toast.LENGTH_SHORT, true).show()
                finish()
            } else {
                t?.message?.let { Toasty.error(this@FeedBackActivity, it, Toast.LENGTH_SHORT, true).show() }
            }
        })
    }
}



```
2、ViewModel

ViewModel 使用ViewModelScope协程来发起网络请求，将结果使用LiveData 发送到上层。

```js
class FeedBackViewModel : ViewModel() {

    var messageLiveData = MutableLiveData<FeedBackResultMessage>()
    private var feedBackResultMessage: FeedBackResultMessage? = null

    fun getFeedBackMessage(content: String) {
        viewModelScope.launch(Dispatchers.IO) {
            val feedBack = Feedback(content)
            feedBack.save(object : SaveListener<String>() {
                override fun done(p0: String?, p1: BmobException?) {
                    feedBackResultMessage = if (p1 == null) {
                        FeedBackResultMessage(
                            FeedBackResultMessage.CODE_SUCCESS,
                            FeedBackResultMessage.MESSAGE_SUCCESS
                        )
                    } else {
                        FeedBackResultMessage(
                            FeedBackResultMessage.CODE_ERROR,
                            FeedBackResultMessage.MESSAGE_ERROR
                        )
                    }
                    messageLiveData.postValue(feedBackResultMessage)
                }
            })
        }
    }
}



```

3、Bean
反馈实体


```js

data class Feedback (var Content : String,
                    var deviceType : String = "android",
                    var userid : String = BmobUser.getCurrentUser(User::class.java).objectId) : BmobObject() //以前项目中使用了Bmob的数据库存储服务


```
反馈结果实体


```js

/*
 * code 0 代表成功
 * code 1 代表失败
 */
data class FeedBackResultMessage (val code : Int, val message: String) {

    companion object {
        const val CODE_SUCCESS : Int = 0
        const val CODE_ERROR : Int = 1

        const val MESSAGE_SUCCESS : String = "反馈成功~~~"
        const val MESSAGE_ERROR : String = "反馈失败~~~,请检查网络"
    }
}


```
**总结**

MVVM优点：

- 降低耦合度

- 数据驱动

- 可以异步线程更新数据

- 易于单元测试

- 方便协同开发等

目前已经使用这种改造方法改造了反馈模块，修改密码模块，发帖模块。后续的话逐渐把整个项目使用MMVM进行改造。