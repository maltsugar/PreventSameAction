# PreventSameAction
Prevent Repeated Actions within the set time，在设置的时间内阻止重复的动作

网上找到的都是button的分类，设置多少时间内不可交互，我的项目需求，有一个通知 可能会同一时间收到多条，收到要去请求未读数量接口，显示红点，这样收到通知就会频繁调用接口。所以网上的都不适合我的项目（也有可能是我没有找到。。。）。就自己写了个宏

##很方便，个人感觉比分类功能强大，而且不止限于button

这个原理其他语言都是通的

<pre>
// 防止多次调用
#define kGYCancelActionInTime(_seconds_) \
static BOOL shouldPrevent; \
if (shouldPrevent) return; \
shouldPrevent = YES; \
dispatch_after(dispatch_time(DISPATCH_TIME_NOW, (int64_t)((_seconds_) * NSEC_PER_SEC)), dispatch_get_main_queue(), ^{ \
    shouldPrevent = NO; \
}); \
</pre>
