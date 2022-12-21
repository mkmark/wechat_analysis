# 微信聊天记录分析

分析微信pc数据库中的信息，详见分析内容

需要numpy pandas

需要提前解密微信数据库，参见[x1hy9/WeChatUserDB](https://github.com/x1hy9/WeChatUserDB)

需要解密的db：

- WeChat Files/[wechat_id]/Msg/ChatMsg.db
- WeChat Files/[wechat_id]/Msg/MicroMsg.db
- WeChat Files/[wechat_id]/Msg/Multi/MSG*.db

全部复制到入[x1hy9/WeChatUserDB](https://github.com/x1hy9/WeChatUserDB)/WIN_WECHAT_DB/ 文件夹解密

需要手动替换main.ipynb中的BASE_PATH为解密输出路径[x1hy9/WeChatUserDB](https://github.com/x1hy9/WeChatUserDB)/DECRYPT_WIN_WECHAT_DB/ 

具体参见main.ipynb

## 分析内容

- msg_cnt 消息条数
- wd_cnt 消息字符总数（表情会占用很多英文字符，比如[Facepalm]笑哭表情）
- cn_wd_cnt（Chinese word count） 消息中文文字总数（相比字符总数更能体现有效信息量）
- wd_pmsg（word per message） 每条消息平均字符数量
- cn_wd_pmsg（Chinese word per message） 每条消息平均中文字符数量
- msg_ratio（message count ratio） "r/s"即="receive/send"即"收到/发出"的消息数量比
- cn_wd_ratio（Chinese word ratio） "收到/发出"的中文字符数量比

表格按降序分别如下排列 取前或后 20 条：

- 我所发出的消息的条数
- 我所收到的消息的条数 去除群聊
- 我所收发的消息的条数 去除群聊
- 高 msg_ratio 去除群聊
- 低 msg_ratio 去除群聊 去除不常联系人(消息条数少于 216)
- 高 cn_wd_ratio 去除群聊
- 低 cn_wd_ratio 去除群聊 去除不常联系人(消息条数少于 216)
