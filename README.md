# ETH2.0-Staking-Service
ETH2.0可乐质押系统，支持ETH及ERC20代币质押并生成锚定币

#### 一、用户质押
1.防止重入漏洞  
2.验证最小质押量、验证代币是否支持质押、验证系统锁定状态、验证是否强制倍数质押  
3.支持ETH、ERC20多币种质押  
4.支持大户、散户质押  
5.每32个ETH生成一笔订单（id唯一）并生成事件，超出或不足32ETH的单独生成订单（mutiple需设置为false）  
6.建立用户-订单的映射关系（为了降低gas采用单向映射）  
7.生成锚定币  

#### 二、用户提取
1.防止重入漏洞  
2.验证当前状态是否可提现、验证当前币种是否存在、验证系统锁定状态、验证本人是否有可提数量，分别验证合约ERC20及ETH余额是否足够提现  
3.销毁锚定币  
4.移除订单信息  
5.区分ETH及ERC20转账方式，给用户提现  

#### 三、转移并创建节点
1.验证资金账户地址不为0、验证是否服务账号在执行操作、验证是否支持转移代币、验证订单id列表是否正确    
2.根据订单id列表计算要转移的代币数量  
3.按币种检查合约余额是否充足  
4.更新订单状态为不可提取（用户无法提现）  
5.转移代币至资金账户  

#### 四、转入并更新状态
1.首先转入需要提现的代币至合约（后端计算好后转入）  
2.更新需要提现的订单的状态为可提取  
3.用户现在可以销毁锚定币提现  

#### 五、管理支持质押的代币列表
1.可添加多个币种及兑换汇率  
2.支持多个币种以不同的兑换率生成锚定币  
3.支持倍数质押、非倍数质押  
4.支持最大最小值  
5.支持兑换汇率设置  

#### 六、系统设置
1.支持锁定充值、提现操作  
2.支持更换资金账户地址  
3.支持更换服务账户地址  
4.支持更换管理账户地址  

#### 七、紧急提现
1.支持紧急提现用户资金至系统设置的资金账户  
