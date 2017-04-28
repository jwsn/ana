ANA —– ANA is Not APP, but Attitude and Ambition Power by WzW team

[用户场景]

场景A

DCR自动化记录测试结果。

背景：协议组经常邀请第三方做DCR测试，自测手机driving测试中的性能问题，通常由第三方手动记录掉话时间，地点和次数。

改善点：

通过ANA，自动记录测试的结果及各种利于分析的信息，使得结果更加准确可靠，避免由于认为失误而造成的多记/漏记，及信息传递有缺失。
由于测试路线较为固定，可以通过多次测试，记录一些已知覆盖盲点作为已知问题点，可过滤一部分已知问题，减少R&D分析负担。
如有必要，可向网络运营商提供相关信息协助改善。
场景B

VOC of MT/MO call failed & RF performance 
背景：经常收到客户VOC，接不到电话/打不出电话/网络信号差，但一般客户提交log时不包含CP log，无法进行深入分析。而且抓log对于客户来说比较困难，也不愿意尝试。

改善点：

通过ANA，记录必要的协议/RF信息，用来判断当前客户所处网络环境状态，并记录所生异常的关键信息，利于判断分析。必要时，可发送相关log到VOC处理邮箱。

[功能模块]

1. 监听MO/MT call模块

Ongoing
主要风险点，需要改动RIL Framework
在发起MO call/接收到MT call，通知控制模块。
2. 数据库模块

Done 
通过contentProvider/contentResolver访问数据库，提供读取保存/读取一条call记录。
提供DcrDAOParser serialize/parse接口将过程中的数据存入xml文件。
3 设置模块

TBD 
提供用户设置参数或选项
如静止测试或者driving call。
4. RF performance模块

TODO
需监听信号消息，获取RF重要信息（RX level，SNR等）。
5. 控制模块

TODO
实现业务流程，接听到MO/MT call消息后，将时间记录，并定时记录DcrDAO信息，在call drop时将记录保存到数据库，将DcrDAO list记录在xml文件。
5. UX模块

主要加分点。
1）显示call drop记录 Done
2）百度地图显示位置移动信息。Done
3）启动引导界面或动画。 Done
4）RF信息显示在界面上，可通过绘制图表显示。Ongoing
5）主界面。作为上一层界面，提供查看call记录，用户设置等入口。TBD
6）其他界面优化，美化。 TBD
6. Log模块

不一定要silent log，可自定义log形式，生成另外文件，结合邮件模块，远程发log。
TBD
7. 发送邮件模块

通过邮件帐号发给指定三星VOC帐号。
TBD
[Call Flow]

监听MO/MT call模块 -->  控制模块 <-- RF performance模块 
                         |
                         |
                         V
                      数据库模块
                         |
                         |
                         V
                       UI模块
NOTE:

作为富有创造力的team，我们都是产品设计师，要主动地多去思考可以改进的地方，积极地去实现好的想法，不断地升级我们的产品，也就是不断地提升自己，这才是我们参赛的意义所在，请共勉之！
