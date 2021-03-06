title: IncomingInvite
---

当有人邀请其他人加入会话时,被邀请者会接受到邀请信息并返回一个 `IncomingInvite` 对象,通过 `InconmingInvite` 对象可以接受（ `accept` ）或拒绝（ `reject` ）邀请。在接受邀请的ConversationCallback中可以获取会话相关信息。

## 方法

### accpet(LocalStream,ConversationCallback)

**定义**   

```java
void accpet(LocalStream localStream,ConversationCallback callback)
```

**说明**

参与者收到加入会话邀请,接受会话邀请。

**参数**

| 参数名 | 描述 |
|---|---|
|localStream|[LocalStream](/api/video/android/local-stream.html),被邀请者通过 `Video.createLocalStream` 获取的本地视频流|
|callback|[ConversationCallback](/api/video/android/conversation-callback.html),会话回调函数,接受时可在 `callBack.onConversation()` 方法中获取到 `conversation` 对象|


**示例**

```java
	//接受邀请
	//localStream=video.createLocalStream(LocalStreamOptions.DEFAULT_OPTIONS, new CompleteListener(){//...});
	incomingInvite.accept(localStream, new ConversationCallback() {
        @Override
        public void onConversation(Conversation conversation, ConversationException exception) {
            //对方接受邀请并成功建立会话,conversation不为空,exception为空
            if (conversation != null) {
                mConversation = conversation;
                //获取到conversation后,设置ConversationListener
                mConversation.setConversationListener(new Conversation.Listener() {
                    //...
                });

            } else {
                //处理会话建立失败逻辑
            }
        }
    });

```

</br>

---

### reject()

**定义**   

```java
void reject()
```

**说明**

收到加入会话邀请的参与者,拒绝会话邀请。

**示例**

```java
	//拒绝邀请
	incomingInvite.reject();
```
