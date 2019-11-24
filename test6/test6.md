<p>目录</p>
<p><a href="#_Toc22118 ">微信小程序甜点商城 2</a></p>
<ol>
<li><a href="#_Toc3481 "> 甜点商城ER模型 2</a></li>
</ol>
<p><a href="#_Toc28190 ">1.1实体模型 2</a></p>
<p><a href="#_Toc31586 ">1.2实体联系模型 4</a></p>
<p><a href="#_Toc17290 ">整个甜点微信小程序的的ER图，如图1-10. 5</a></p>
<ol start="2">
<li><a href="#_Toc26089 "> 甜点商城数据表的设计 5</a></li>
<li><a href="#_Toc28214 "> 创建数据库 7</a></li>
</ol>
<p><a href="#_Toc10050 ">3.1配置插接式数据库PDB 7</a></p>
<p><a href="#_Toc26041 ">3.2通过Oracle SQL Developer连接数据库 8</a></p>
<ol start="4">
<li><a href="#_Toc3886 "> 用户创建与空间分配 8</a></li>
<li><a href="#_Toc16178 "> 创建表，约束和索引 10</a></li>
<li><a href="#_Toc22832 "> 创建触发器、序列和视图 14</a></li>
<li><a href="#_Toc16264 "> 创建程序包、函数和过程 15</a></li>
<li><a href="#_Toc6201 "> 数据库备份 20</a></li>
</ol>
<p><a href="#_Toc12523 ">8.1开始全备份 20</a></p>
<p><a href="#_Toc27829 ">8.2备份后修改数据 27</a></p>
<p><a href="#_Toc7465 ">8.3删除数据库文件，模拟数据库文件损坏 27</a></p>
<p><a href="#_Toc16384 ">8.4数据库完全恢复 29</a></p>
<p><a href="#_Toc23505 ">8.4.1重启损坏的数据库到mount状态 29</a></p>
<p><a href="#_Toc22671 ">8.4.2开始恢复数据库 30</a></p>
<p><a href="#_Toc6709 ">8.5查询数据是否恢复 30</a></p>
<p><a href="#_Toc29775 ">9.数据库DataGuard设计 31</a></p>
<p><a href="#_Toc29906 ">9.1oracle 12C dataguard搭建环境（主从库相同，从库只装软件不建库） 31</a></p>
<p><a href="#_Toc17157 ">9.2 dataguard主库参数配置 32</a></p>
<p><a href="#_Toc13480 ">9.3.配置两个数据库的网络参数文件tnsname.ora和listener.ora 34</a></p>
<p><a href="#_Toc10426 ">9.3.1配置tnsnames.ora参数文件 34</a></p>
<p><a href="#_Toc6270 ">9.3.2配置监听文件 35</a></p>
<p><a href="#_Toc12407 ">9.4.配置数据库参数文件 36</a></p>
<p><a href="#_Toc4398 ">9.5.启动standby database到nomount状态 37</a></p>
<p><a href="#_Toc6614 ">9.5.1检查tns连接名是否正常(主备库均需要检查) 37</a></p>
<p><a href="#_Toc20841 ">9.5.2启动备库 37</a></p>
<p><a href="#_Toc57 ">参考文献 38</a></p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p><a name="_Toc22118"></a><strong><strong>微信小程序甜点商城</strong></strong></p>
<ol>
<li><a name="_Toc3481"></a>甜点商城ER模型</li>
</ol>
<p>本系统基于微信小程序的甜点商城系统，主要针对于大学生线上购买的小程序，服务于特定的某一个商家。如果商家在美团或则是饿了么平台上来卖东西的话，则会收取昂贵的平台费，本来大学生的消费就不是很高，再加上平台费，可能在外卖上点甜点就不是很现实。如果有了微信小程序的甜点线上商城，少了平台费，就可以在价格上面带来很大的优势。</p>
<p>&nbsp;</p>
<p><a name="_Toc28190"></a>1.1实体模型&nbsp;</p>
<p>根据应用场景分析，共有5个原始的实体(Entity)，它们是管理员、用户、会员、订单和甜点。</p>
<p>管理员(admin)包括管理员id（admin_id）、联系电话（tel）、管理员名（admin_username）和管理员密码(password)，如图1-1。
</p>
<p>&nbsp;</p>
<p><img src='./images/1-1.png'>图 1-1 管理员（admin）实体</p>
<p>&nbsp;</p>
<p>甜点（dessert）包括甜点id（dessert_id）、甜点图片（image）、甜点名称（name）、甜点简介（Introduction）、甜点价格（price）。管理员可对甜点进行增删查改，主要进行商品的价钱的更新。甜点的实体，如图1-2。
</p>
<p>&nbsp;</p>
<p><img src='./images/1-2.png'>图 1-2&nbsp;甜点（dessert）实体</p>
<p>用户（user）包括用户id（user_id）、用户名（username）、联系电话（tel）、用户地址（address）。在每次用户下单后，订单上面需要根据用户id或是用户名对该订单的详细记录写进数据库。用户实体，如图1-3。</p>
<p>&nbsp;</p>
<p><img src='./images/1-3.png'>图 1-3&nbsp;用户（user）实体</p>
<p>会员（member）包括会员id（member_id）、用户id（user_id）、会员购买时间（member_start）、会员截止时间（member_end）、购买时长（member_time）。可以根据会员的结束时间来提醒用户是否续费，根据购买时长来计算会员的截止时间。会员实体，如图1-4。</p>
<p>&nbsp;</p>
<p><img src='./images/1-4.png'>图 1-4&nbsp;会员（member）实体</p>
<p>订单（order）包括订单编号（order_id）、用户id（user_id）、用户名（username）、用户地址（address）、下单时间（order_time）、订单总金额（total_price）。订单实体，如图1-5。</p>
<p>&nbsp;</p>
<p><img src='./images/1-5.png'>图 1-5&nbsp;订单（order）实体</p>
<p>&nbsp;</p>
<p><a name="_Toc31586"></a>1.2实体联系模型&nbsp;</p>
<p>管理员和甜点的关系是一对多的关系，在这个商城系统，只有一个管理员账号，每个员工可以登录这个管理员账号对商品的甜点信息进行增删查改。</p>
<p>&nbsp;</p>
<p><img src='./images/1-6.png'>图 1-6 管理员与甜点的关系简图</p>
<p>用户和甜点的关系是多对多，一个用户可以购买多个甜品，同一种甜品可以被多个用户购买。</p>
<p>&nbsp;</p>
<p><img src='./images/1-7.png'>图 1-7 用户和甜点的关系简图</p>
<p>用户和会员的关系是多对一，一个用户只能购买一个会员。</p>
<p>&nbsp;</p>
<p><img src='./images/1-8.png'>图 1-8 用户和会员的关系简图</p>
<p>用户和订单的关系是多对多，每个人的下单没有限制，一个人可以下多个订单。因为一个用户的下单地址可能不一样，所以在这里每一个订单都必须绑定自己的订单地址。</p>
<p>&nbsp;</p>
<p><img src='./images/1-9.png'>图 1-9 用户和订单的关系简图</p>
<p><a name="_Toc17290"></a>整个甜点微信小程序的的ER图，如图1-10.</p>
<p>&nbsp;</p>
<p><img src='./images/1-10.png'>图 1-10 &nbsp;甜点商城ER图</p>
<p>&nbsp;</p>
<ol start="2">
<li><a name="_Toc26089"></a>甜点商城数据表的设计</li>
</ol>
<p>ER模型建立好以后，我们就可以设计Oracle的关系表了。在独立实体中找出主要属性设置为主键，比如在订单表中，订单编号（order_id）是主键。由关系派生出的实体要加入外键关系，如订单中要加入外键用户id（user_id）属性。</p>
<p>管理员（admin）表包括管理员id（admin_id）、联系电话(tel)、管理员名（admin_name）、管理员密码（password）,见表2-1。</p>
<p>表 2-1 &nbsp;甜点商城管理员ADMIN</p>
<table>
<tbody>
<tr>
<td width="111">
<p><strong><strong>字段名</strong></strong></p>
</td>
<td width="111">
<p><strong><strong>数据类型</strong></strong></p>
</td>
<td width="111">
<p><strong><strong>可以为空</strong></strong></p>
</td>
<td width="111">
<p><strong><strong>注释</strong></strong></p>
</td>
<td width="111">
<p><strong><strong>备注</strong></strong></p>
</td>
</tr>
<tr>
<td width="111">
<p>admin_id</p>
</td>
<td width="111">
<p>varchar</p>
</td>
<td width="111">
<p>no</p>
</td>
<td width="111">
<p>管理员ID</p>
</td>
<td width="111">
<p>主键</p>
</td>
</tr>
<tr>
<td width="111">
<p>tel</p>
</td>
<td width="111">
<p>varchar</p>
</td>
<td width="111">
<p>no</p>
</td>
<td width="111">
<p>管理员联系方式</p>
</td>
<td width="111">
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="111">
<p>admin_name</p>
</td>
<td width="111">
<p>varchar</p>
</td>
<td width="111">
<p>no</p>
</td>
<td width="111">
<p>管理员名</p>
</td>
<td width="111">
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="111">
<p>password</p>
</td>
<td width="111">
<p>varchar</p>
</td>
<td width="111">
<p>no</p>
</td>
<td width="111">
<p>管理员密码</p>
</td>
<td width="111">
<p>&nbsp;</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>用户表USERS包括用户ID（user_id）、用户的联系方式（tel）、用户名（username）、用户的联系地址（address），其中用户的联系地址可以有多个地址，用逗号（，）隔开，见表2-2。</p>
<p>表 2-2 &nbsp;甜点商城用户USERNAME</p>
<table>
<tbody>
<tr>
<td width="111">
<p><strong><strong>字段名</strong></strong></p>
</td>
<td width="111">
<p><strong><strong>数据类型</strong></strong></p>
</td>
<td width="111">
<p><strong><strong>可以为空</strong></strong></p>
</td>
<td width="111">
<p><strong><strong>注释</strong></strong></p>
</td>
<td width="111">
<p><strong><strong>备注</strong></strong></p>
</td>
</tr>
<tr>
<td width="111">
<p>user_id</p>
</td>
<td width="111">
<p>varchar</p>
</td>
<td width="111">
<p>no</p>
</td>
<td width="111">
<p>用户ID</p>
</td>
<td width="111">
<p>主键</p>
</td>
</tr>
<tr>
<td width="111">
<p>tel</p>
</td>
<td width="111">
<p>varchar</p>
</td>
<td width="111">
<p>no</p>
</td>
<td width="111">
<p>用户联系方式</p>
</td>
<td width="111">
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="111">
<p>username</p>
</td>
<td width="111">
<p>varchar</p>
</td>
<td width="111">
<p>no</p>
</td>
<td width="111">
<p>用户名</p>
</td>
<td width="111">
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="111">
<p>address</p>
</td>
<td width="111">
<p>varchar</p>
</td>
<td width="111">
<p>yes</p>
</td>
<td width="111">
<p>用户地址</p>
</td>
<td width="111">
<p>可以有多个地址</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>甜点表DESERT包括甜点ID（desert_id）、甜点图片（desert_image）、甜点名称（desert_name）、甜点简介（introduce）、甜点价格（price），见表2-3。</p>
<p>表 2-3 甜点商城甜点DESERT</p>
<table>
<tbody>
<tr>
<td width="111">
<p><strong><strong>字段名</strong></strong></p>
</td>
<td width="111">
<p><strong><strong>数据类型</strong></strong></p>
</td>
<td width="111">
<p><strong><strong>可以为空</strong></strong></p>
</td>
<td width="111">
<p><strong><strong>注释</strong></strong></p>
</td>
<td width="111">
<p><strong><strong>备注</strong></strong></p>
</td>
</tr>
<tr>
<td width="111">
<p>desert_id</p>
</td>
<td width="111">
<p>varchar</p>
</td>
<td width="111">
<p>no</p>
</td>
<td width="111">
<p>甜点ID</p>
</td>
<td width="111">
<p>主键</p>
</td>
</tr>
<tr>
<td width="111">
<p>desert_image</p>
</td>
<td width="111">
<p>varchar</p>
</td>
<td width="111">
<p>no</p>
</td>
<td width="111">
<p>甜点图片</p>
</td>
<td width="111">
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="111">
<p>desert_name</p>
</td>
<td width="111">
<p>varchar</p>
</td>
<td width="111">
<p>no</p>
</td>
<td width="111">
<p>甜点名称</p>
</td>
<td width="111">
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="111">
<p>introduce</p>
</td>
<td width="111">
<p>varchar</p>
</td>
<td width="111">
<p>yes</p>
</td>
<td width="111">
<p>甜点简介</p>
</td>
<td width="111">
<p>可以为空</p>
</td>
</tr>
<tr>
<td width="111">
<p>price</p>
</td>
<td width="111">
<p>float</p>
</td>
<td width="111">
<p>no</p>
</td>
<td width="111">
<p>甜点价格</p>
</td>
<td width="111">
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="111">
<p>type</p>
</td>
<td width="111">
<p>varchar</p>
</td>
<td width="111">
<p>no</p>
</td>
<td width="111">
<p>甜点的类型</p>
</td>
<td width="111">
<p>种类</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>会员表MEMBER包括会员ID（member_id）、会员购买时间（member_start）、会员截止时间（member_end）、购买时长（member_time）、用户ID（user_id），见表1-4。</p>
<p>&nbsp;</p>
<p>表 2-4 甜点商城会员MEMBER</p>
<table>
<tbody>
<tr>
<td width="111">
<p><strong><strong>字段名</strong></strong></p>
</td>
<td width="111">
<p><strong><strong>数据类型</strong></strong></p>
</td>
<td width="111">
<p><strong><strong>可以为空</strong></strong></p>
</td>
<td width="111">
<p><strong><strong>注释</strong></strong></p>
</td>
<td width="111">
<p><strong><strong>备注</strong></strong></p>
</td>
</tr>
<tr>
<td width="111">
<p>member_id</p>
</td>
<td width="111">
<p>varchar</p>
</td>
<td width="111">
<p>no</p>
</td>
<td width="111">
<p>会员ID</p>
</td>
<td width="111">
<p>主键</p>
</td>
</tr>
<tr>
<td width="111">
<p>member_start</p>
</td>
<td width="111">
<p>date</p>
</td>
<td width="111">
<p>no</p>
</td>
<td width="111">
<p>会员开始时间</p>
</td>
<td width="111">
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="111">
<p>member_end</p>
</td>
<td width="111">
<p>date</p>
</td>
<td width="111">
<p>no</p>
</td>
<td width="111">
<p>会员结束时间</p>
</td>
<td width="111">
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="111">
<p>member_time</p>
</td>
<td width="111">
<p>varchar</p>
</td>
<td width="111">
<p>no</p>
</td>
<td width="111">
<p>会员总时间</p>
</td>
<td width="111">
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="111">
<p>user_id</p>
</td>
<td width="111">
<p>varchar</p>
</td>
<td width="111">
<p>no</p>
</td>
<td width="111">
<p>用户id</p>
</td>
<td width="111">
<p>外键</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>订单（order）包括订单编号（order_id）、用户id（user_id）、用户名（username）、用户地址（address）、下单时间（order_time）、订单总金额（total_price）。订单实体，如表2-5。</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>表 2-5 甜点商城订单ORDER</p>
<table>
<tbody>
<tr>
<td width="111">
<p><strong><strong>字段名</strong></strong></p>
</td>
<td width="111">
<p><strong><strong>数据类型</strong></strong></p>
</td>
<td width="111">
<p><strong><strong>可以为空</strong></strong></p>
</td>
<td width="111">
<p><strong><strong>注释</strong></strong></p>
</td>
<td width="111">
<p><strong><strong>备注</strong></strong></p>
</td>
</tr>
<tr>
<td width="111">
<p>order_id</p>
</td>
<td width="111">
<p>varchar</p>
</td>
<td width="111">
<p>no</p>
</td>
<td width="111">
<p>订单ID</p>
</td>
<td width="111">
<p>主键</p>
</td>
</tr>
<tr>
<td width="111">
<p>user_id</p>
</td>
<td width="111">
<p>varchar</p>
</td>
<td width="111">
<p>no</p>
</td>
<td width="111">
<p>用户ID</p>
</td>
<td width="111">
<p>外键</p>
</td>
</tr>
<tr>
<td width="111">
<p>username</p>
</td>
<td width="111">
<p>varchar</p>
</td>
<td width="111">
<p>no</p>
</td>
<td width="111">
<p>用户名</p>
</td>
<td width="111">
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="111">
<p>address</p>
</td>
<td width="111">
<p>varchar</p>
</td>
<td width="111">
<p>no</p>
</td>
<td width="111">
<p>订单地址</p>
</td>
<td width="111">
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="111">
<p>order_time</p>
</td>
<td width="111">
<p>date</p>
</td>
<td width="111">
<p>no</p>
</td>
<td width="111">
<p>下单时间</p>
</td>
<td width="111">
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="111">
<p>total_price</p>
</td>
<td width="111">
<p>float</p>
</td>
<td width="111">
<p>no</p>
</td>
<td width="111">
<p>订单总金额</p>
</td>
<td width="111">
<p>&nbsp;</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<ol start="3">
<li><a name="_Toc28214"></a>创建数据库</li>
</ol>
<p><a name="_Toc10050"></a>3.1配置插接式数据库PDB</p>
<p>配置插接式数据库PDB可以通过SQL语句创建插接式数据库，在创建时可以选择创建一个新的空的PDB，不包含任何数据；也可以选择一个现有的PDB克隆成另一个PDB，所谓克隆，是指将原有的PDB的用户信息和数据信息一起复制到新的PDB中，这也是Oracle 12C的重要特性。</p>
<p>在这儿，我们通过dbca工具创建插接式数据库，首先以Oracle用户登录，运行dbca命令，然后根据提示操作，要注意输入正确的数据库目录、PDB数据库名称以管理员信息。</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p><img src='./images/3-1.png'>图 3-1&nbsp;甜点商城通过dbca创建插接式数据库</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p><a name="_Toc26041"></a>3.2通过Oracle SQL Developer连接数据库</p>
<p>Oracle SQL Developer是一个免费的GUI图形界面的管理和开发工具，可以提高工作效率并简化数据库开发任务。SQL Developer可以在没有安装数据库的客户端上运行，支持Windows、Linux、Mac系统。</p>
<p>可以在Oracle官网上下载，直接使用，无需安装。Oracle SQL Developer是基于Java的应用程序，如果客户端没有安装Java，就需要下载自带有Java的SQL Developer，如果客户端已经安装了Java，就可以下载不带Java版本。</p>
<p>&nbsp;</p>
<p><img src='./images/3-2.png'>图 3-2&nbsp;甜点商城通过SQL Developer连接Oracle</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<ol start="4">
<li><a name="_Toc3886"></a>用户创建与空间分配</li>
</ol>
<p>表的结构设计之后，还需要考虑用户和空间的分配问题。我们需要为系统新建一个用户（NICETONG）。另外还需要为甜点商城系统创建一个新表空间NICETONG用户存储订单记录。</p>
<p>下面是SYSTEM用户创建的一个表空间nicetong的命令，注意给nicetong表空间分配了两个数据文件：pdbtest_nicetong1.dbf和pdbtest_nicetong2.dbf，这两个数据文件初始大小都是100M，所以表空间的初始大小是200M。</p>
<table>
<tbody>
<tr>
<td width="568">
<p>create tablespace nicetong</p>
<p>datafile</p>
<p>'/home/oracle/app/oracle/oradata/orcl/pdborcl/pdbtest_nicetong1.dbf'</p>
<p>size 100M AUTOEXTEND ON NEXT 256M MAXSIZE UNLIMITED,</p>
<p>'/home/oracle/app/oracle/oradata/orcl/pdborcl/pdbtest_nicetong2.dbf'</p>
<p>size 100M AUTOEXTEND ON NEXT 256M MAXSIZE UNLIMITED</p>
<p>EXTENT MANAGEMENT LOCAL SEGMENT SPACE MANAGEMENT AUTO;</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p><img src='./images/4-1.png'>图 4-1&nbsp;甜点商城创建表空间nicetong</p>
<p>表空间nicetong创建完成之后，就可以创建用户了。我们可以为本系统设计的用户名称是nicetong。用户创建之后，给用户nicetong分配表空间nicetong的使用配额，再分配角色CONNECT和RESOURCE，以便该用户可以连接数据库，可以创建资源（表，过程，序列等资源对象），最后再分配一个系统权限：&rdquo;CREATE VIEW&rdquo;，以便该用户可以创建视图。</p>
<table>
<tbody>
<tr>
<td width="568">
<p>//给用户nicetong</p>
<p>alter &nbsp;user nicetong &nbsp;DEFAULT TABLESPACE "USERS" TEMPORARY TABLESPACE "TEMP";</p>
<p>-- QUOTAS</p>
<p>ALTER USER nicetong QUOTA UNLIMITED ON USERS;</p>
<p>ALTER USER nicetong QUOTA UNLIMITED ON nicetong;</p>
<p>-- ROLES</p>
<p>GRANT "CONNECT" TO nicetong WITH ADMIN OPTION;</p>
<p>GRANT "RESOURCE" TO nicetong WITH ADMIN OPTION;</p>
<p>ALTER USER nicetong DEFAULT ROLE "CONNECT","RESOURCE";</p>
<p>-- SYSTEM PRIVILEGES</p>
<p>GRANT CREATE VIEW TO nicetong WITH ADMIN OPTION;</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p><img src='./images/4-2.png'>图 4-2&nbsp;甜点商城创建用户以及分配表空间</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>到现在，我们有了两个表空间USERS（原有的）和NICETONG（新建的）。这里我们假定店主的销售订单非常多，订单表的记录非常大，可能上千万条记录，所以我们把ORDERS表设计为基于REDER_DATA的分区表，以加快局部时间范围的查询速度。存储空间的分如表4-1。</p>
<p>&nbsp;</p>
<p>表 4-1&nbsp;甜点商城存储空间分配</p>
<table>
<tbody>
<tr>
<td width="106">
<p><strong><strong>表</strong></strong></p>
</td>
<td width="216">
<p><strong><strong>表空间USERS</strong></strong></p>
</td>
<td width="213">
<p><strong><strong>表空间NICETONG</strong></strong></p>
</td>
</tr>
<tr>
<td width="106">
<p>ORDERS</p>
</td>
<td width="216">
<p>存储全部数据</p>
</td>
<td width="213">
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="106">
<p>USERS</p>
</td>
<td width="216">
<p>存储全部数据</p>
</td>
<td width="213">
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="106">
<p>ADMIN</p>
</td>
<td width="216">
<p>存储全部数据</p>
</td>
<td width="213">
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="106">
<p>MEMBER</p>
</td>
<td width="216">
<p>存储2019年前（不含）的数据</p>
</td>
<td width="213">
<p>存储2019年前（不含）的数据</p>
</td>
</tr>
<tr>
<td width="106">
<p>DESERT</p>
</td>
<td width="216">
<p>存储全部数据</p>
</td>
<td width="213">
<p>&nbsp;</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<ol start="5">
<li><a name="_Toc16178"></a>创建表，约束和索引</li>
</ol>
<p>用户和空间分配完成后，可以创建表，约束和索引了。创建表的命令是 CREATE TABLE，由于命令参数和选项很复杂，命令行数非常多，所以这里就不将创建表的 DDL语句全部写出来。这里仅对 ORDERS 和 DESERT两个表的创建作一些说明，ORDERS 表按分区存储，分区类型选择&ldquo;RANG&rdquo;范围分区，创建 ORDERS 表的部分语句是：</p>
<table>
<tbody>
<tr>
<td width="568">
<p>create table ORDERS</p>
<p>(</p>
<p>order_id &nbsp;VARCHAR2(10) PRIMARY KEY NOT NULL,</p>
<p>user_id VARCHAR2(10) NOT NULL,</p>
<p>username VARCHAR2(9) NOT NULL,</p>
<p>address &nbsp;VARCHAR2(10) NOT NULL,</p>
<p>order_time DATE NOT NULL,</p>
<p>total_price FLOAT NOT NULL</p>
<p>);</p>
<p>CREATE TABLE DESERT(</p>
<p>desert_id VARCHAR2(10) PRIMARY KEY NOT NULL,</p>
<p>desert_image VARCHAR2(14) NOT NULL,</p>
<p>desert_name VARCHAR2(13) NOT NULL,</p>
<p>introduce VARCHAR2(14) NOT NULL,</p>
<p>price FLOAT NOT NULL,</p>
<p>type VARCHAR2(14) NOT NULL</p>
<p>);</p>
<p>CREATE TABLE MEMBER</p>
<p>(</p>
<p>member_id VARCHAR2(10) PRIMARY KEY NOT NULL,</p>
<p>member_start &nbsp;DATE NOT NULL,</p>
<p>member_end DATE NOT NULL ,</p>
<p>member_time VARCHAR2(10) NOT NULL,</p>
<p>user_id VARCHAR2(10) NOT NULL</p>
<p>);</p>
<p>CREATE TABLE USERS</p>
<p>(</p>
<p>user_id VARCHAR2(10) PRIMARY KEY NOT NULL,</p>
<p>tel VARCHAR2(10) NOT NULL,</p>
<p>username VARCHAR2(10) NOT NULL,</p>
<p>address VARCHAR2(10)</p>
<p>);</p>
<p>CREATE TABLE ADMIN</p>
<p>(</p>
<p>admin_id VARCHAR2(10) PRIMARY KEY NOT NULL,</p>
<p>tel VARCHAR2(10) NOT NULL,</p>
<p>admin_name VARCHAR2(10) NOT NULL,</p>
<p>password VARCHAR2(10) NOT NULL</p>
<p>);</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p><img src='./images/5-1.png'>图 5-1&nbsp;甜点商城创建表及其约束</p>
<p>&nbsp;</p>
<p>在这个命令中，核心的语句是&ldquo;PARTITION BY RANGE (order_time)&rdquo;，表示按订单时间 ORDER_TIME&nbsp;的范围进行分区。分区 PARTITION_BEFORE_2019存储订单时间小于2019年 的订单记录，这个分区存储在表空间 USERS 中 ,而分区PARTITION_BEFORE_2020&nbsp;存储的是订单时间小于 2020&nbsp;年的订单记录，由于有分区PARTITION_BEFORE_2019&nbsp;的存在，PARTITION_BEFORE_2020&nbsp;分区实际只存储 2019年一年的记录。创建 ORDERS表的部分语句如下：</p>
<table>
<tbody>
<tr>
<td width="568">
<p>create table ORDERS</p>
<p>(</p>
<p>order_id &nbsp;VARCHAR2(10) PRIMARY KEY NOT NULL,</p>
<p>user_id VARCHAR2(10) NOT NULL,</p>
<p>username VARCHAR2(9) NOT NULL,</p>
<p>address &nbsp;VARCHAR2(10) NOT NULL,</p>
<p>order_time DATE NOT NULL,</p>
<p>total_price FLOAT NOT NULL</p>
<p>)</p>
<p>TABLESPACE USERS</p>
<p>PCTFREE 10 INITRANS 1</p>
<p>STORAGE ( &nbsp;&nbsp;BUFFER_POOL DEFAULT )</p>
<p>NOCOMPRESS NOPARALLEL</p>
<p>PARTITION BY RANGE (order_time)</p>
<p>(</p>
<p>&nbsp;PARTITION PARTITION_BEFORE_2016 VALUES LESS THAN (</p>
<p>&nbsp;TO_DATE(' 2019-01-01 00:00:00', 'SYYYY-MM-DD HH24:MI:SS',</p>
<p>&nbsp;'NLS_CALENDAR=GREGORIAN'))</p>
<p>&nbsp;NOLOGGING</p>
<p>&nbsp;TABLESPACE USERS</p>
<p>&nbsp;PCTFREE 10</p>
<p>&nbsp;INITRANS 1</p>
<p>&nbsp;STORAGE</p>
<p>(</p>
<p>&nbsp;INITIAL 8388608</p>
<p>&nbsp;NEXT 1048576</p>
<p>&nbsp;MINEXTENTS 1</p>
<p>&nbsp;MAXEXTENTS UNLIMITED</p>
<p>&nbsp;BUFFER_POOL DEFAULT</p>
<p>)</p>
<p>NOCOMPRESS NO INMEMORY &nbsp;</p>
<p>, PARTITION PARTITION_BEFORE_2017 VALUES LESS THAN (</p>
<p>TO_DATE(' 2020-01-01 00:00:00', 'SYYYY-MM-DD HH24:MI:SS',</p>
<p>'NLS_CALENDAR=GREGORIAN'))</p>
<p>NOLOGGING</p>
<p>);</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>向订单表中加入50000条数据</p>
<table>
<tbody>
<tr>
<td width="568">
<p>declare</p>
<p>&nbsp;&nbsp;dt date;</p>
<p>BEGIN</p>
<p>for i IN 1..50000 LOOP</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dt:=to_date('2015-3-2','yyyy-mm-dd')+(i mod 60); --PARTITION_2015</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;INSERT INTO orders (order_id, user_id, username,address,order_time,total_price)</p>
<p>&nbsp;&nbsp;VALUES ('001'+i,'6515','nicetong','sichuan',to_date('2016-3-2','yyyy-mm-dd'),66.0);</p>
<p>&nbsp;&nbsp;END LOOP;</p>
<p>END;</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>查询插入的数据</p>
<table>
<tbody>
<tr>
<td width="568">
<p>select * from orders;</p>
<p>select count(order_id) from orders;</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p><img src='./images/5-2-1.png'><img src='./images/5-2-2.png'>图 5-2 向order表中插入50000条数据</p>
<p>因为订单表的数据很多，我们在这里可以为订单表建立索引。</p>
<p>为user_id建立索引</p>
<table>
<tbody>
<tr>
<td width="568">
<p>create index info_order_id on orders (user_id);</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p><img src='./images/5-3.png'>图 5-3&nbsp;甜点商城创建索引</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<ol start="6">
<li><a name="_Toc22832"></a>创建触发器、序列和视图</li>
</ol>
<p>&nbsp;</p>
<p>主要用于级联更新，如更新users表中的users_id时，member表的user_id也更新。</p>
<table>
<tbody>
<tr>
<td width="568">
<p>CREATE OR REPLACE TRIGGER cascade_trigger</p>
<p>AFTER UPDATE OF user_id ON users</p>
<p>FOR EACH ROW</p>
<p>BEGIN</p>
<p>&nbsp;&nbsp;UPDATE member SET user_id=:new.user_id WHERE user_id=:old.user_id;</p>
<p>END;</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p><img src='./images/6-1.png'>图 6-1&nbsp;甜点商城创建级联更新用户id的触发器</p>
<p>创建序列：为orders表创建自增序列。</p>
<table>
<tbody>
<tr>
<td width="568">
<p>CREATE SEQUENCE orders_sequence</p>
<p>INCREMENT BY 1 &nbsp;&nbsp;</p>
<p>START WITH 1 &nbsp;&nbsp;&nbsp;&nbsp;</p>
<p>NOMAXVALUE &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</p>
<p>NOCYCLE &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</p>
<p>CACHE 10;</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p><img src='./images/6-2.png'>图 6-2 甜点商城创建序列</p>
<p>&nbsp;</p>
<ol start="7">
<li><a name="_Toc16264"></a>创建程序包、函数和过程</li>
</ol>
<p>7.1创建一个存储过程，修改admin表中的admin_name字段。</p>
<table>
<tbody>
<tr>
<td width="568">
<p>create or replace procedure update_admin</p>
<p>(</p>
<p>v_admin_id &nbsp;varchar2,</p>
<p>v_admin_name &nbsp;varchar2</p>
<p>) is</p>
<p>begin</p>
<p>update admin set admin_name=v_admin_name where admin_id=v_admin_id; &nbsp;</p>
<p>end update_admin;</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p><img src='./images/7-1.png'>图 7-1&nbsp;甜点商城创建更新管理员密码的存储过程</p>
<p>测试存储过程：</p>
<table>
<tbody>
<tr>
<td width="568">
<p>select * from admin;</p>
<p>exec &nbsp;update_admin('001','test');</p>
<p>select * from admin;</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p><img src='./images/7-2.png'>图 7-2&nbsp;甜点商城测试更新管理员密码的存储过程</p>
<p>&nbsp;</p>
<p>7.2创建一个存储过程，修改admin表中的tel字段。</p>
<table>
<tbody>
<tr>
<td width="568">
<p>create or replace procedure update_adminTel</p>
<p>(</p>
<p>v_admin_id &nbsp;varchar2,</p>
<p>v_admin_tel varchar2</p>
<p>) is</p>
<p>begin</p>
<p>update admin set tel=v_admin_tel where admin_id=v_admin_id; &nbsp;</p>
<p>end update_adminTel;</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p><img src='./images/7-3.png'>图 7-3&nbsp;甜点商城创建更新管理员联系电话的存储过程</p>
<p>测试存储过程：</p>
<table>
<tbody>
<tr>
<td width="568">
<p>select * from admin;</p>
<p>exec &nbsp;update_adminTel('001','123456');</p>
<p>select * from admin;</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p><img src='./images/7-4.png'>图 7-4&nbsp;甜点商城测试更新管理员联系电话的存储过程</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>7.3创建一个存储过程，查看admin表中根据admin_id查询出admin的name</p>
<table>
<tbody>
<tr>
<td width="568">
<p>create or replace procedure admin_out_name</p>
<p>&nbsp;(</p>
<p>&nbsp;v_admin_id in VARCHAR2,</p>
<p>&nbsp;v_name out VARCHAR2</p>
<p>&nbsp;) is</p>
<p>vname &nbsp;VARCHAR2(10) ;</p>
<p>&nbsp;begin</p>
<p>&nbsp;select admin_name into vname from admin where admin_id=v_admin_id;</p>
<p>&nbsp;v_name:=vname;</p>
<p>&nbsp;end;</p>
</td>
</tr>
</tbody>
</table>
<p><strong><strong>&nbsp;</strong></strong></p>
<p><img src='./images/7-5.png'>图 7-5&nbsp;甜点商城创建查看管理员name的存储过程</p>
<p>测试存储过程：</p>
<table>
<tbody>
<tr>
<td width="568">
<p>var vname VARCHAR2</p>
<p>exec &nbsp;admin_out_name('001',:vname);</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p><img src='./images/7-6.png'>图 7-6&nbsp;甜点商城测试查看管理员name的存储过程</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>7.4创建程序包</p>
<p>本系统设计了一些函数及过程，共用的一些程序包放在程序包MyPack中。其他的程序包放在自己的包中。包用于组合逻辑相关的过程和函数，它由包规范和包体两个部分组成。包规范用于定义公用的常量、变量、过程和函数，创建包规范可以使用CREATE PACKAGE命令，创建包体可以使用CREATE PACKAGE BODY。</p>
<table>
<tbody>
<tr>
<td width="568">
<p>&nbsp;create package admin_pkg is</p>
<p>&nbsp;procedure admin_update_Tel(v_admin_id varchar2,v_admin_tel varchar2);</p>
<p>&nbsp;function admin_get_name(v_admin_id varchar2) return varchar2;</p>
<p>&nbsp;end;</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p><img src='./images/7-7.png'>图 7-7&nbsp;甜点商城创建关于admin表的程序包</p>
<p>创建关于admin表程序包admin_pkg的包体：</p>
<table>
<tbody>
<tr>
<td width="568">
<p>create or replace package body admin_pkg</p>
<p>is</p>
<p>&nbsp;&nbsp;&nbsp;procedure admin_update_Tel</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;(</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;v_admin_id &nbsp;varchar2,</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;v_admin_tel varchar2</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;) is</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;begin</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;update admin set tel=v_admin_tel where admin_id=v_admin_id; &nbsp;</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;end;</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;function admin_get_name</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;(</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;v_admin_id varchar2</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;)</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;return varchar2 is</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;vname varchar2(10);</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;begin</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;select admin_name into vname from admin where admin_id= v_admin_id;</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;return vname;</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p><img src='./images/7-8.png'>图 7-8 甜点商城创建关于admin表的程序包的包体</p>
<p>注意：</p>
<p>在此提示，在没有创建包规范就创建包体，会失败，要使用包，必须先创建包规范，然后在创建包体当要调用包的过程和函数时，在过程和函数的名称前加上包名作为前缀（包名.子程序名称），而如果要访问其他方案的包时需要在包的名称前加上方案的名称（方案名称.包名.子程序名称）</p>
<p>测试admin_pkg的程序包：</p>
<table>
<tbody>
<tr>
<td width="568">
<p>select admin_pkg.admin_get_name('001') from dual;</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p><img src='./images/7-9.png'>图 7-9 甜点商城测试admin程序包的函数</p>
<table>
<tbody>
<tr>
<td width="568">
<p>exec admin_pkg.admin_update_Tel('001','3333');</p>
<p>select * from admin where admin_id='001';</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p><img src='./images/7-10.png'>图 7-10甜点商城测试admin程序包的函数</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<ol start="8">
<li><a name="_Toc6201"></a>数据库备份</li>
</ol>
<p>本实验使用老师的虚拟机，通过rman_level0.sh和rman_level1.sh脚本对数据库进行全备份和全恢复，在数据库出现异常时候，不损失任何数据！</p>
<p><a name="_Toc12523"></a>8.1开始全备份</p>
<p>通过rman_level0.sh和rman_level1.sh脚本对数据库进行全备份和全恢复。</p>
<table>
<tbody>
<tr>
<td width="568">
<p>[oracle@oracle-pc ~]$ cat rman_level0.sh</p>
<p>[oracle@oracle-pc ~]$ ./rman_level0.sh</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p><img src='./images/8-1.png'>图 8-1 甜点商城开始全备份</p>
<p>每天定时开始增量备份（可选）</p>
<table>
<tbody>
<tr>
<td width="568">
<p>[oracle@oracle-pc ~]$ cat rman_level1.sh</p>
<p>[oracle@oracle-pc ~]$ ./rman_level1.sh</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p><img src='./images/8-2.png'>图 8-2 甜点商城每天定时开始增量备份</p>
<p>&nbsp;</p>
<p>查看备份文件</p>
<table>
<tbody>
<tr>
<td width="568">
<p>[oracle@oracle-pc ~]$ cd rman_backup</p>
<p>[oracle@oracle-pc rman_backup]$ ls</p>
<p>arclv0_ORCL_20191124_9fuhmdgk_1_1.bak &nbsp;dblv1_ORCL_20191124_9iuhmdp6_1_1.bak</p>
<p>arclv1_ORCL_20191124_9huhmdp5_1_1.bak &nbsp;dblv1_ORCL_20191124_9juhmdrr_1_1.bak</p>
<p>arclv1_ORCL_20191124_9muhmdud_1_1.bak &nbsp;dblv1_ORCL_20191124_9kuhmdtj_1_1.bak</p>
<p>c-1392946895-20191124-01 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;lv0_20191111-003303_L0.log</p>
<p>dblv0_ORCL_20191124_9buhmd53_1_1.bak &nbsp;&nbsp;lv0_20191124-155112_L0.log</p>
<p>dblv0_ORCL_20191124_9cuhmd92_1_1.bak &nbsp;&nbsp;lv1_20191111-003650_L0.log</p>
<p>dblv0_ORCL_20191124_9duhmdce_1_1.bak &nbsp;&nbsp;lv1_20191124-160237_L0.log</p>
<p>dblv0_ORCL_20191124_9euhmde6_1_1.bak</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p><img src='./images/8-3.png'>图 8-3 甜点商城查看备份文件</p>
<p>查看备份文件的内容</p>
<table>
<tbody>
<tr>
<td width="568">
<p>[oracle@oracle-pc ~]$ &nbsp;rman target /</p>
<p>&nbsp;</p>
<p>Recovery Manager: Release 12.1.0.2.0 - Production on 星期日 11月 24 16:11:44 2019</p>
<p>&nbsp;</p>
<p>Copyright (c) 1982, 2014, Oracle and/or its affiliates. &nbsp;All rights reserved.</p>
<p>&nbsp;</p>
<p>connected to target database: ORCL (DBID=1392946895)</p>
<p>&nbsp;</p>
<p>RMAN&gt; list backup;</p>
<p>&nbsp;</p>
<p>using target database control file instead of recovery catalog</p>
<p>&nbsp;</p>
<p>List of Backup Sets</p>
<p>===================</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>BS Key &nbsp;Type LV Size &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Device Type Elapsed Time Completion Time</p>
<p>------- ---- -- ---------- ----------- ------------ ---------------</p>
<p>251 &nbsp;&nbsp;&nbsp;&nbsp;Incr 0 &nbsp;215.20M &nbsp;&nbsp;&nbsp;DISK &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;00:01:59 &nbsp;&nbsp;&nbsp;&nbsp;24-11月-19 &nbsp;&nbsp;&nbsp;</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;BP Key: 251 &nbsp;&nbsp;Status: AVAILABLE &nbsp;Compressed: YES &nbsp;Tag: TAG20191124T155203</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Piece Name: /home/oracle/rman_backup/dblv0_ORCL_20191124_9buhmd53_1_1.bak</p>
<p>&nbsp;&nbsp;List of Datafiles in backup set 251</p>
<p>&nbsp;&nbsp;Container ID: 3, PDB Name: PDBORCL</p>
<p>&nbsp;&nbsp;File LV Type Ckp SCN &nbsp;&nbsp;&nbsp;Ckp Time &nbsp;&nbsp;Name</p>
<p>&nbsp;&nbsp;---- -- ---- ---------- ---------- ----</p>
<p>&nbsp;&nbsp;8 &nbsp;&nbsp;&nbsp;0 &nbsp;Incr 47254373 &nbsp;&nbsp;24-11月-19 /home/oracle/app/oracle/oradata/orcl/pdborcl/system01.dbf</p>
<p>&nbsp;&nbsp;9 &nbsp;&nbsp;&nbsp;0 &nbsp;Incr 47254373 &nbsp;&nbsp;24-11月-19 /home/oracle/app/oracle/oradata/orcl/pdborcl/sysaux01.dbf</p>
<p>&nbsp;&nbsp;10 &nbsp;&nbsp;0 &nbsp;Incr 47254373 &nbsp;&nbsp;24-11月-19 /home/oracle/app/oracle/oradata/orcl/pdborcl/SAMPLE_SCHEMA_users01.dbf</p>
<p>&nbsp;&nbsp;11 &nbsp;&nbsp;0 &nbsp;Incr 47254373 &nbsp;&nbsp;24-11月-19 /home/oracle/app/oracle/oradata/orcl/pdborcl/example01.dbf</p>
<p>&nbsp;&nbsp;12 &nbsp;&nbsp;0 &nbsp;Incr 47254373 &nbsp;&nbsp;24-11月-19 /home/oracle/app/oracle/oradata/orcl/pdborcl/pdbtest_users02_1.dbf</p>
<p>&nbsp;&nbsp;13 &nbsp;&nbsp;0 &nbsp;Incr 47254373 &nbsp;&nbsp;24-11月-19 /home/oracle/app/oracle/oradata/orcl/pdborcl/pdbtest_users02_2.dbf</p>
<p>&nbsp;&nbsp;16 &nbsp;&nbsp;0 &nbsp;Incr 47254373 &nbsp;&nbsp;24-11月-19 /home/oracle/app/oracle/oradata/orcl/pdborcl/pdbtest_users02_3.dbf</p>
<p>&nbsp;&nbsp;17 &nbsp;&nbsp;0 &nbsp;Incr 47254373 &nbsp;&nbsp;24-11月-19 /home/oracle/app/oracle/oradata/orcl/pdborcl/pdbtest_users02_4.dbf</p>
<p>&nbsp;&nbsp;77 &nbsp;&nbsp;0 &nbsp;Incr 47254373 &nbsp;&nbsp;24-11月-19 /home/oracle/app/oracle/oradata/orcl/pdborcl/pdbtest_users03_1.dbf</p>
<p>&nbsp;&nbsp;78 &nbsp;&nbsp;0 &nbsp;Incr 47254373 &nbsp;&nbsp;24-11月-19 /home/oracle/app/oracle/oradata/orcl/pdborcl/pdbtest_users03_2.dbf</p>
<p>&nbsp;</p>
<p>BS Key &nbsp;Type LV Size &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Device Type Elapsed Time Completion Time</p>
<p>------- ---- -- ---------- ----------- ------------ ---------------</p>
<p>252 &nbsp;&nbsp;&nbsp;&nbsp;Incr 0 &nbsp;369.77M &nbsp;&nbsp;&nbsp;DISK &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;00:01:42 &nbsp;&nbsp;&nbsp;&nbsp;24-11月-19 &nbsp;&nbsp;&nbsp;</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;BP Key: 252 &nbsp;&nbsp;Status: AVAILABLE &nbsp;Compressed: YES &nbsp;Tag: TAG20191124T155203</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Piece Name: /home/oracle/rman_backup/dblv0_ORCL_20191124_9cuhmd92_1_1.bak</p>
<p>&nbsp;&nbsp;List of Datafiles in backup set 252</p>
<p>&nbsp;&nbsp;File LV Type Ckp SCN &nbsp;&nbsp;&nbsp;Ckp Time &nbsp;&nbsp;Name</p>
<p>&nbsp;&nbsp;---- -- ---- ---------- ---------- ----</p>
<p>&nbsp;&nbsp;1 &nbsp;&nbsp;&nbsp;0 &nbsp;Incr 47254431 &nbsp;&nbsp;24-11月-19 /home/oracle/app/oracle/oradata/orcl/system01.dbf</p>
<p>&nbsp;&nbsp;3 &nbsp;&nbsp;&nbsp;0 &nbsp;Incr 47254431 &nbsp;&nbsp;24-11月-19 /home/oracle/app/oracle/oradata/orcl/sysaux01.dbf</p>
<p>&nbsp;&nbsp;4 &nbsp;&nbsp;&nbsp;0 &nbsp;Incr 47254431 &nbsp;&nbsp;24-11月-19 /home/oracle/app/oracle/oradata/orcl/undotbs01.dbf</p>
<p>&nbsp;&nbsp;6 &nbsp;&nbsp;&nbsp;0 &nbsp;Incr 47254431 &nbsp;&nbsp;24-11月-19 /home/oracle/app/oracle/oradata/orcl/users01.dbf</p>
<p>&nbsp;</p>
<p>BS Key &nbsp;Type LV Size &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Device Type Elapsed Time Completion Time</p>
<p>------- ---- -- ---------- ----------- ------------ ---------------</p>
<p>253 &nbsp;&nbsp;&nbsp;&nbsp;Incr 0 &nbsp;160.44M &nbsp;&nbsp;&nbsp;DISK &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;00:00:47 &nbsp;&nbsp;&nbsp;&nbsp;24-11月-19 &nbsp;&nbsp;&nbsp;</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;BP Key: 253 &nbsp;&nbsp;Status: AVAILABLE &nbsp;Compressed: YES &nbsp;Tag: TAG20191124T155203</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Piece Name: /home/oracle/rman_backup/dblv0_ORCL_20191124_9duhmdce_1_1.bak</p>
<p>&nbsp;&nbsp;List of Datafiles in backup set 253</p>
<p>&nbsp;&nbsp;Container ID: 4, PDB Name: LOCALHOST_PDBORCL_TEST</p>
<p>&nbsp;&nbsp;File LV Type Ckp SCN &nbsp;&nbsp;&nbsp;Ckp Time &nbsp;&nbsp;Name</p>
<p>&nbsp;&nbsp;---- -- ---- ---------- ---------- ----</p>
<p>&nbsp;&nbsp;79 &nbsp;&nbsp;0 &nbsp;Incr 47254493 &nbsp;&nbsp;24-11月-19 /home/oracle/app/oracle/oradata/orcl/localhost_pdborcl_test/system01.dbf</p>
<p>&nbsp;&nbsp;80 &nbsp;&nbsp;0 &nbsp;Incr 47254493 &nbsp;&nbsp;24-11月-19 /home/oracle/app/oracle/oradata/orcl/localhost_pdborcl_test/sysaux01.dbf</p>
<p>&nbsp;&nbsp;81 &nbsp;&nbsp;0 &nbsp;Incr 47254493 &nbsp;&nbsp;24-11月-19 /home/oracle/app/oracle/oradata/orcl/localhost_pdborcl_test/localhost_pdborcl_test_users01.dbf</p>
<p>&nbsp;&nbsp;82 &nbsp;&nbsp;0 &nbsp;Incr 47254493 &nbsp;&nbsp;24-11月-19 /home/oracle/app/oracle/oradata/orcl/pdborcl/pdbtest_nicetong1.dbf</p>
<p>&nbsp;&nbsp;83 &nbsp;&nbsp;0 &nbsp;Incr 47254493 &nbsp;&nbsp;24-11月-19 /home/oracle/app/oracle/oradata/orcl/pdborcl/pdbtest_nicetong2.dbf</p>
<p>&nbsp;</p>
<p>BS Key &nbsp;Type LV Size &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Device Type Elapsed Time Completion Time</p>
<p>------- ---- -- ---------- ----------- ------------ ---------------</p>
<p>254 &nbsp;&nbsp;&nbsp;&nbsp;Incr 0 &nbsp;157.08M &nbsp;&nbsp;&nbsp;DISK &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;00:01:11 &nbsp;&nbsp;&nbsp;&nbsp;24-11月-19 &nbsp;&nbsp;&nbsp;</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;BP Key: 254 &nbsp;&nbsp;Status: AVAILABLE &nbsp;Compressed: YES &nbsp;Tag: TAG20191124T155203</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Piece Name: /home/oracle/rman_backup/dblv0_ORCL_20191124_9euhmde6_1_1.bak</p>
<p>&nbsp;&nbsp;List of Datafiles in backup set 254</p>
<p>&nbsp;&nbsp;Container ID: 2, PDB Name: PDB$SEED</p>
<p>&nbsp;&nbsp;File LV Type Ckp SCN &nbsp;&nbsp;&nbsp;Ckp Time &nbsp;&nbsp;Name</p>
<p>&nbsp;&nbsp;---- -- ---- ---------- ---------- ----</p>
<p>&nbsp;&nbsp;5 &nbsp;&nbsp;&nbsp;0 &nbsp;Incr 1819408 &nbsp;&nbsp;&nbsp;01-12月-14 /home/oracle/app/oracle/oradata/orcl/pdbseed/system01.dbf</p>
<p>&nbsp;&nbsp;7 &nbsp;&nbsp;&nbsp;0 &nbsp;Incr 1819408 &nbsp;&nbsp;&nbsp;01-12月-14 /home/oracle/app/oracle/oradata/orcl/pdbseed/sysaux01.dbf</p>
<p>&nbsp;</p>
<p>BS Key &nbsp;Size &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Device Type Elapsed Time Completion Time</p>
<p>------- ---------- ----------- ------------ ---------------</p>
<p>255 &nbsp;&nbsp;&nbsp;&nbsp;67.50K &nbsp;&nbsp;&nbsp;&nbsp;DISK &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;00:00:00 &nbsp;&nbsp;&nbsp;&nbsp;24-11月-19 &nbsp;&nbsp;&nbsp;</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;BP Key: 255 &nbsp;&nbsp;Status: AVAILABLE &nbsp;Compressed: YES &nbsp;Tag: TAG20191124T155811</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Piece Name: /home/oracle/rman_backup/arclv0_ORCL_20191124_9fuhmdgk_1_1.bak</p>
<p>&nbsp;</p>
<p>&nbsp;&nbsp;List of Archived Logs in backup set 255</p>
<p>&nbsp;&nbsp;Thrd Seq &nbsp;&nbsp;&nbsp;&nbsp;Low SCN &nbsp;&nbsp;&nbsp;Low Time &nbsp;&nbsp;Next SCN &nbsp;&nbsp;Next Time</p>
<p>&nbsp;&nbsp;---- ------- ---------- ---------- ---------- ---------</p>
<p>&nbsp;&nbsp;1 &nbsp;&nbsp;&nbsp;1616 &nbsp;&nbsp;&nbsp;47254352 &nbsp;&nbsp;24-11月-19 47254544 &nbsp;&nbsp;24-11月-19</p>
<p>&nbsp;</p>
<p>BS Key &nbsp;Size &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Device Type Elapsed Time Completion Time</p>
<p>------- ---------- ----------- ------------ ---------------</p>
<p>257 &nbsp;&nbsp;&nbsp;&nbsp;1.91M &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DISK &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;00:00:00 &nbsp;&nbsp;&nbsp;&nbsp;24-11月-19 &nbsp;&nbsp;&nbsp;</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;BP Key: 257 &nbsp;&nbsp;Status: AVAILABLE &nbsp;Compressed: YES &nbsp;Tag: TAG20191124T160245</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Piece Name: /home/oracle/rman_backup/arclv1_ORCL_20191124_9huhmdp5_1_1.bak</p>
<p>&nbsp;</p>
<p>&nbsp;&nbsp;List of Archived Logs in backup set 257</p>
<p>&nbsp;&nbsp;Thrd Seq &nbsp;&nbsp;&nbsp;&nbsp;Low SCN &nbsp;&nbsp;&nbsp;Low Time &nbsp;&nbsp;Next SCN &nbsp;&nbsp;Next Time</p>
<p>&nbsp;&nbsp;---- ------- ---------- ---------- ---------- ---------</p>
<p>&nbsp;&nbsp;1 &nbsp;&nbsp;&nbsp;1616 &nbsp;&nbsp;&nbsp;47254352 &nbsp;&nbsp;24-11月-19 47254544 &nbsp;&nbsp;24-11月-19</p>
<p>&nbsp;&nbsp;1 &nbsp;&nbsp;&nbsp;1617 &nbsp;&nbsp;&nbsp;47254544 &nbsp;&nbsp;24-11月-19 47255360 &nbsp;&nbsp;24-11月-19</p>
<p>&nbsp;</p>
<p>BS Key &nbsp;Type LV Size &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Device Type Elapsed Time Completion Time</p>
<p>------- ---- -- ---------- ----------- ------------ ---------------</p>
<p>258 &nbsp;&nbsp;&nbsp;&nbsp;Incr 1 &nbsp;328.00K &nbsp;&nbsp;&nbsp;DISK &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;00:01:24 &nbsp;&nbsp;&nbsp;&nbsp;24-11月-19 &nbsp;&nbsp;&nbsp;</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;BP Key: 258 &nbsp;&nbsp;Status: AVAILABLE &nbsp;Compressed: YES &nbsp;Tag: TAG20191124T160246</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Piece Name: /home/oracle/rman_backup/dblv1_ORCL_20191124_9iuhmdp6_1_1.bak</p>
<p>&nbsp;&nbsp;List of Datafiles in backup set 258</p>
<p>&nbsp;&nbsp;Container ID: 3, PDB Name: PDBORCL</p>
<p>&nbsp;&nbsp;File LV Type Ckp SCN &nbsp;&nbsp;&nbsp;Ckp Time &nbsp;&nbsp;Name</p>
<p>&nbsp;&nbsp;---- -- ---- ---------- ---------- ----</p>
<p>&nbsp;&nbsp;8 &nbsp;&nbsp;&nbsp;1 &nbsp;Incr 47255370 &nbsp;&nbsp;24-11月-19 /home/oracle/app/oracle/oradata/orcl/pdborcl/system01.dbf</p>
<p>&nbsp;&nbsp;9 &nbsp;&nbsp;&nbsp;1 &nbsp;Incr 47255370 &nbsp;&nbsp;24-11月-19 /home/oracle/app/oracle/oradata/orcl/pdborcl/sysaux01.dbf</p>
<p>&nbsp;&nbsp;10 &nbsp;&nbsp;1 &nbsp;Incr 47255370 &nbsp;&nbsp;24-11月-19 /home/oracle/app/oracle/oradata/orcl/pdborcl/SAMPLE_SCHEMA_users01.dbf</p>
<p>&nbsp;&nbsp;11 &nbsp;&nbsp;1 &nbsp;Incr 47255370 &nbsp;&nbsp;24-11月-19 /home/oracle/app/oracle/oradata/orcl/pdborcl/example01.dbf</p>
<p>&nbsp;&nbsp;12 &nbsp;&nbsp;1 &nbsp;Incr 47255370 &nbsp;&nbsp;24-11月-19 /home/oracle/app/oracle/oradata/orcl/pdborcl/pdbtest_users02_1.dbf</p>
<p>&nbsp;&nbsp;13 &nbsp;&nbsp;1 &nbsp;Incr 47255370 &nbsp;&nbsp;24-11月-19 /home/oracle/app/oracle/oradata/orcl/pdborcl/pdbtest_users02_2.dbf</p>
<p>&nbsp;&nbsp;16 &nbsp;&nbsp;1 &nbsp;Incr 47255370 &nbsp;&nbsp;24-11月-19 /home/oracle/app/oracle/oradata/orcl/pdborcl/pdbtest_users02_3.dbf</p>
<p>&nbsp;&nbsp;17 &nbsp;&nbsp;1 &nbsp;Incr 47255370 &nbsp;&nbsp;24-11月-19 /home/oracle/app/oracle/oradata/orcl/pdborcl/pdbtest_users02_4.dbf</p>
<p>&nbsp;&nbsp;77 &nbsp;&nbsp;1 &nbsp;Incr 47255370 &nbsp;&nbsp;24-11月-19 /home/oracle/app/oracle/oradata/orcl/pdborcl/pdbtest_users03_1.dbf</p>
<p>&nbsp;&nbsp;78 &nbsp;&nbsp;1 &nbsp;Incr 47255370 &nbsp;&nbsp;24-11月-19 /home/oracle/app/oracle/oradata/orcl/pdborcl/pdbtest_users03_2.dbf</p>
<p>&nbsp;</p>
<p>BS Key &nbsp;Type LV Size &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Device Type Elapsed Time Completion Time</p>
<p>------- ---- -- ---------- ----------- ------------ ---------------</p>
<p>259 &nbsp;&nbsp;&nbsp;&nbsp;Incr 1 &nbsp;2.34M &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DISK &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;00:00:49 &nbsp;&nbsp;&nbsp;&nbsp;24-11月-19 &nbsp;&nbsp;&nbsp;</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;BP Key: 259 &nbsp;&nbsp;Status: AVAILABLE &nbsp;Compressed: YES &nbsp;Tag: TAG20191124T160246</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Piece Name: /home/oracle/rman_backup/dblv1_ORCL_20191124_9juhmdrr_1_1.bak</p>
<p>&nbsp;&nbsp;List of Datafiles in backup set 259</p>
<p>&nbsp;&nbsp;File LV Type Ckp SCN &nbsp;&nbsp;&nbsp;Ckp Time &nbsp;&nbsp;Name</p>
<p>&nbsp;&nbsp;---- -- ---- ---------- ---------- ----</p>
<p>&nbsp;&nbsp;1 &nbsp;&nbsp;&nbsp;1 &nbsp;Incr 47255497 &nbsp;&nbsp;24-11月-19 /home/oracle/app/oracle/oradata/orcl/system01.dbf</p>
<p>&nbsp;&nbsp;3 &nbsp;&nbsp;&nbsp;1 &nbsp;Incr 47255497 &nbsp;&nbsp;24-11月-19 /home/oracle/app/oracle/oradata/orcl/sysaux01.dbf</p>
<p>&nbsp;&nbsp;4 &nbsp;&nbsp;&nbsp;1 &nbsp;Incr 47255497 &nbsp;&nbsp;24-11月-19 /home/oracle/app/oracle/oradata/orcl/undotbs01.dbf</p>
<p>&nbsp;&nbsp;6 &nbsp;&nbsp;&nbsp;1 &nbsp;Incr 47255497 &nbsp;&nbsp;24-11月-19 /home/oracle/app/oracle/oradata/orcl/users01.dbf</p>
<p>&nbsp;</p>
<p>BS Key &nbsp;Type LV Size &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Device Type Elapsed Time Completion Time</p>
<p>------- ---- -- ---------- ----------- ------------ ---------------</p>
<p>260 &nbsp;&nbsp;&nbsp;&nbsp;Incr 1 &nbsp;208.00K &nbsp;&nbsp;&nbsp;DISK &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;00:00:23 &nbsp;&nbsp;&nbsp;&nbsp;24-11月-19 &nbsp;&nbsp;&nbsp;</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;BP Key: 260 &nbsp;&nbsp;Status: AVAILABLE &nbsp;Compressed: YES &nbsp;Tag: TAG20191124T160246</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Piece Name: /home/oracle/rman_backup/dblv1_ORCL_20191124_9kuhmdtj_1_1.bak</p>
<p>&nbsp;&nbsp;List of Datafiles in backup set 260</p>
<p>&nbsp;&nbsp;Container ID: 4, PDB Name: LOCALHOST_PDBORCL_TEST</p>
<p>&nbsp;&nbsp;File LV Type Ckp SCN &nbsp;&nbsp;&nbsp;Ckp Time &nbsp;&nbsp;Name</p>
<p>&nbsp;&nbsp;---- -- ---- ---------- ---------- ----</p>
<p>&nbsp;&nbsp;79 &nbsp;&nbsp;1 &nbsp;Incr 47255538 &nbsp;&nbsp;24-11月-19 /home/oracle/app/oracle/oradata/orcl/localhost_pdborcl_test/system01.dbf</p>
<p>&nbsp;&nbsp;80 &nbsp;&nbsp;1 &nbsp;Incr 47255538 &nbsp;&nbsp;24-11月-19 /home/oracle/app/oracle/oradata/orcl/localhost_pdborcl_test/sysaux01.dbf</p>
<p>&nbsp;&nbsp;81 &nbsp;&nbsp;1 &nbsp;Incr 47255538 &nbsp;&nbsp;24-11月-19 /home/oracle/app/oracle/oradata/orcl/localhost_pdborcl_test/localhost_pdborcl_test_users01.dbf</p>
<p>&nbsp;&nbsp;82 &nbsp;&nbsp;1 &nbsp;Incr 47255538 &nbsp;&nbsp;24-11月-19 /home/oracle/app/oracle/oradata/orcl/pdborcl/pdbtest_nicetong1.dbf</p>
<p>&nbsp;&nbsp;83 &nbsp;&nbsp;1 &nbsp;Incr 47255538 &nbsp;&nbsp;24-11月-19 /home/oracle/app/oracle/oradata/orcl/pdborcl/pdbtest_nicetong2.dbf</p>
<p>&nbsp;</p>
<p>BS Key &nbsp;Size &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Device Type Elapsed Time Completion Time</p>
<p>------- ---------- ----------- ------------ ---------------</p>
<p>261 &nbsp;&nbsp;&nbsp;&nbsp;90.00K &nbsp;&nbsp;&nbsp;&nbsp;DISK &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;00:00:00 &nbsp;&nbsp;&nbsp;&nbsp;24-11月-19 &nbsp;&nbsp;&nbsp;</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;BP Key: 261 &nbsp;&nbsp;Status: AVAILABLE &nbsp;Compressed: YES &nbsp;Tag: TAG20191124T160533</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Piece Name: /home/oracle/rman_backup/arclv1_ORCL_20191124_9muhmdud_1_1.bak</p>
<p>&nbsp;</p>
<p>&nbsp;&nbsp;List of Archived Logs in backup set 261</p>
<p>&nbsp;&nbsp;Thrd Seq &nbsp;&nbsp;&nbsp;&nbsp;Low SCN &nbsp;&nbsp;&nbsp;Low Time &nbsp;&nbsp;Next SCN &nbsp;&nbsp;Next Time</p>
<p>&nbsp;&nbsp;---- ------- ---------- ---------- ---------- ---------</p>
<p>&nbsp;&nbsp;1 &nbsp;&nbsp;&nbsp;1618 &nbsp;&nbsp;&nbsp;47255360 &nbsp;&nbsp;24-11月-19 47255551 &nbsp;&nbsp;24-11月-19</p>
<p>&nbsp;</p>
<p>BS Key &nbsp;Type LV Size &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Device Type Elapsed Time Completion Time</p>
<p>------- ---- -- ---------- ----------- ------------ ---------------</p>
<p>262 &nbsp;&nbsp;&nbsp;&nbsp;Full &nbsp;&nbsp;&nbsp;17.77M &nbsp;&nbsp;&nbsp;&nbsp;DISK &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;00:00:00 &nbsp;&nbsp;&nbsp;&nbsp;24-11月-19 &nbsp;&nbsp;&nbsp;</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;BP Key: 262 &nbsp;&nbsp;Status: AVAILABLE &nbsp;Compressed: NO &nbsp;Tag: TAG20191124T160534</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Piece Name: /home/oracle/rman_backup/c-1392946895-20191124-01</p>
<p>&nbsp;&nbsp;SPFILE Included: Modification time: 24-11月-19</p>
<p>&nbsp;&nbsp;SPFILE db_unique_name: ORCL</p>
<p>&nbsp;&nbsp;Control File Included: Ckp SCN: 47255560 &nbsp;&nbsp;&nbsp;&nbsp;Ckp time: 24-11月-19</p>
<p>&nbsp;</p>
<p>RMAN&gt;</p>
</td>
</tr>
</tbody>
</table>
<p>由上面的"list backup;" 输出可以看出，备份集中的文件内容是：</p>
<p>/home/oracle/rman_backup/dblv0_ORCL_20191120_d7uhb2ap_1_1.bak 是插接数据库PDBORCL的备份集</p>
<p>/home/oracle/rman_backup/dblv0_ORCL_20191120_d8uhb2c6_1_1.bak 是ORCL的备份集</p>
<p>/home/oracle/rman_backup/dblv0_ORCL_20191120_d9uhb2ei_1_1.bak是PDB$SEED的备份集</p>
<p>/home/oracle/rman_backup/arclv0_ORCL_20191120_dauhb2fm_1_1.bak是归档文件的备份集</p>
<p>/home/oracle/rman_backup/c-1392946895-20191120-01是参数文件(SPFILE)和控制文件(Control File)的备份集</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p><a name="_Toc27829"></a>8.2备份后修改数据</p>
<table>
<tbody>
<tr>
<td width="568">
<p>[oracle@oracle-pc ~]$ sqlplus study/123@pdborcl</p>
<p>SQL&gt; create table t1 (id number,name varchar2(50));</p>
<p>Table created.</p>
<p>SQL&gt; insert into t1 values(1,'zhang');1 row created.</p>
<p>SQL&gt; commit;Commit complete.</p>
<p>SQL&gt; select * from t1;</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ID NAME---------- --------------------------------------------------</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1 zhang</p>
<p>SQL&gt; exit</p>
<p>&nbsp;</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p><img src='./images/8-4.png'>图 8-4 甜点商城备份后修改文件</p>
<p><a name="_Toc7465"></a>8.3删除数据库文件，模拟数据库文件损坏</p>
<table>
<tbody>
<tr>
<td width="568">
<p>[oracle@oracle-pc~]$rm&nbsp;/home/oracle/app/oracle/oradata/orcl/pdborcl/SAMPLE_SCHEMA_users01.dbf</p>
</td>
</tr>
</tbody>
</table>
<p>删除数据库文件后修改数据</p>
<p>删除数据文件后，仍然可以增加一条数据。这是因为增加的数据并没有写入数据文件，而是写到了日志文件中。如果增加的数据较多的时候，就会出问题了。</p>
<table>
<tbody>
<tr>
<td width="568">
<p>SQL&gt; insert into t1 values(2,'wang');</p>
<p>1 row created.</p>
<p>SQL&gt; commit;</p>
<p>Commit complete.</p>
<p>SQL&gt; select * from t1;</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ID NAME</p>
<p>---------- --------------------------------------------------</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2 wang</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1 zhang</p>
<p>SQL&gt; &nbsp;declare</p>
<p>&nbsp;&nbsp;2 &nbsp;&nbsp;n number;</p>
<p>&nbsp;&nbsp;3 &nbsp;begin</p>
<p>&nbsp;&nbsp;4 &nbsp;&nbsp;for n in 1..10000 loop</p>
<p>&nbsp;&nbsp;5 &nbsp;&nbsp;insert into t1 values(n,'name'||n);</p>
<p>&nbsp;&nbsp;6 &nbsp;&nbsp;end loop;</p>
<p>&nbsp;&nbsp;7 &nbsp;end;</p>
<p>&nbsp;&nbsp;8 &nbsp;/</p>
<p>&nbsp;declare</p>
<p>*</p>
<p>ERROR at line 1:</p>
<p>ORA-01116: 打开数据库文件 10 时出错 ORA-01110:</p>
<p>数据文件 10: '/home/oracle/app/oracle/oradata/orcl/pdborcl/SAMPLE_SCHEMA_users01.dbf'</p>
<p>ORA-27041: 无法打开文件</p>
<p>Linux-x86_64 Error: 2: No such file or directory</p>
<p>Additional information: 3</p>
<p>ORA-06512: 在 line 5</p>
<p>SQL&gt; select * from t1;</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ID NAME</p>
<p>---------- --------------------------------------------------</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2 wang</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1 zhang</p>
<p>&nbsp;</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p><img src='./images/8-5.png'>图 8-5 甜点商城删除数据库文件</p>
<p>&nbsp;</p>
<p><a name="_Toc16384"></a>8.4数据库完全恢复</p>
<p><a name="_Toc23505"></a>8.4.1重启损坏的数据库到mount状态</p>
<p>通过shutdown immediate无法正常关闭数据库，只能通过shutdown abort强制关闭。然后将数据库启动到mount状态。</p>
<table>
<tbody>
<tr>
<td width="568">
<p>[oracle@oracle-pc ~]$ sqlplus / as sysdba</p>
<p>SQL*Plus: Release 12.1.0.2.0 Production on 星期日 11月 24 16:25:29 2019</p>
<p>Copyright (c) 1982, 2014, Oracle. &nbsp;All rights reserved.</p>
<p>Connected to:</p>
<p>Oracle Database 12c Enterprise Edition Release 12.1.0.2.0 - 64bit Production</p>
<p>With the Partitioning, OLAP, Advanced Analytics and Real Application Testing options</p>
<p>Session altered.</p>
<p>SQL&gt; shutdown immediate</p>
<p>ORA-01116: 打开数据库文件 10 时出错</p>
<p>ORA-01110: 数据文件 10: '/home/oracle/app/oracle/oradata/orcl/pdborcl/SAMPLE_SCHEMA_users01.dbf'</p>
<p>ORA-27041: 无法打开文件</p>
<p>Linux-x86_64 Error: 2: No such file or directory</p>
<p>Additional information: 3</p>
<p>SQL&gt; &nbsp;shutdown abort</p>
<p>ORACLE instance shut down.</p>
<p>SQL&gt; &nbsp;startup mount</p>
<p>ORACLE instance started.</p>
<p>Total System Global Area 1577058304 bytes</p>
<p>Fixed Size &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2924832 bytes</p>
<p>Variable Size &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;738201312 bytes</p>
<p>Database Buffers &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;654311424 bytes</p>
<p>Redo Buffers &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;13848576 bytes</p>
<p>In-Memory Area &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;167772160 bytes</p>
<p>Database mounted.</p>
<p>SQL&gt; exit</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p><img src='./images/8-6.png'>图 8-6 甜点商城重启损坏的数据库到mount状态</p>
<p><a name="_Toc22671"></a>8.4.2开始恢复数据库</p>
<table>
<tbody>
<tr>
<td width="568">
<p>[oracle@oracle-pc ~]$ rman target /</p>
<p>第一步：</p>
<p>RMAN&gt; restore database ;</p>
<p>第二步：</p>
<p>RMAN&gt; recover database;</p>
<p>第三步：</p>
<p>RMAN&gt; alter database open;</p>
<p>第四步：</p>
<p>RMAN&gt; exit</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p><img src='./images/8-7.png'>图 8-7 甜点商城开始恢复数据库</p>
<p>&nbsp;</p>
<p><a name="_Toc6709"></a>8.5查询数据是否恢复<img src='./images/8-7-2.png'></p>
<table>
<tbody>
<tr>
<td width="568">
<p>[oracle@oracle-pc ~]$ sqlplus study/123@pdborcl</p>
<p>SQL&gt; select * from t1;</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ID NAME</p>
<p>---------- --------------------------------------------------</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1 zhang</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2 wang</p>
<p>SQL&gt;</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>由以上查询结果可见，数据100%恢复了!</p>
<p><a name="_Toc29775"></a>9.数据库DataGuard设计</p>
<p><a name="_Toc29906"></a>9.1oracle 12C dataguard搭建环境（主从库相同，从库只装软件不建库）</p>
<table>
<tbody>
<tr>
<td width="568">
<p>[oracle@oracle-pc ~]$ &nbsp;more /etc/redhat-release</p>
<p>CentOS release 6.9 (Final)</p>
<p>[oracle@oracle-pc ~]$ sqlplus</p>
<p>SQL*Plus: Release 12.1.0.2.0 Production on 星期日 11月 24 16:59:13 2019</p>
<p>Copyright (c) 1982, 2014, Oracle. &nbsp;All rights reserved.</p>
<p>Enter user-name: system</p>
<p>Enter password: ***</p>
<p>Last Successful login time: 星期日 11月 24 2019 12:38:12 +08:00</p>
<p>Connected to:</p>
<p>Oracle Database 12c Enterprise Edition Release 12.1.0.2.0 - 64bit Production</p>
<p>With the Partitioning, OLAP, Advanced Analytics and Real Application Testing options</p>
<p>Session altered.</p>
<p>SQL&gt; &nbsp;SELECT * FROM V$VERSION;</p>
<p>BANNER &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;CON_ID</p>
<p>-------------------------------------------------------------------------------- ----------</p>
<p>Oracle Database 12c Enterprise Edition Release 12.1.0.2.0 - 64bit Production &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;0</p>
<p>PL/SQL Release 12.1.0.2.0 - Production &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;0</p>
<p>CORE 12.1.0.2.0 Production &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;0</p>
<p>TNS for Linux: Version 12.1.0.2.0 - Production &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;0</p>
<p>NLSRTL Version 12.1.0.2.0 - Production &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;0</p>
<p>SQL&gt;</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p><img src='./images/9-1.png'>图 9-1 甜点商城查看OS和ORACLE配置信息</p>
<p><a name="_Toc17157"></a>9.2 dataguard主库参数配置</p>
<p>9.2.1检查主库状态，pdb是否为open</p>
<table>
<tbody>
<tr>
<td width="568">
<p>[oracle@oracle-pc ~]$ sqlplus / as sysdba</p>
<p>SQL*Plus: Release 12.1.0.2.0 Production on 星期日 11月 24 17:08:52 2019</p>
<p>Copyright (c) 1982, 2014, Oracle. &nbsp;All rights reserved.</p>
<p>Connected to:</p>
<p>Oracle Database 12c Enterprise Edition Release 12.1.0.2.0 - 64bit Production</p>
<p>With the Partitioning, OLAP, Advanced Analytics and Real Application Testing options</p>
<p>Session altered.</p>
<p>SQL&gt; show pdbs</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;CON_ID CON_NAME &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;OPEN MODE &nbsp;RESTRICTED</p>
<p>---------- ------------------------------ ---------- ----------</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2 PDB$SEED &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;READ ONLY &nbsp;NO</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3 PDBORCL &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;READ WRITE NO</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;4 LOCALHOST_PDBORCL_TEST &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;READ WRITE NO</p>
<p>SQL&gt;</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p><img src='./images/9-2.png'>图 9-2 甜点商城查看检查主库状态</p>
<p>9.2.2检查主库是否开启force_logging，否则要执行以下命令</p>
<table>
<tbody>
<tr>
<td width="568">
<p>SQL&gt; select force_logging from v$database;</p>
<p>SQL&gt; &nbsp;alter database force logging;</p>
<p>Database altered.</p>
<p>SQL&gt; select force_logging from v$database;</p>
<p>FORCE_LOGGING</p>
<p>---------------------------------------</p>
<p>YES</p>
<p>SQL&gt;</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p><img src='./images/9-3.png'>图 9-3 甜点商城查看检查主库是否开启force_logging</p>
<p>9.2.3检查主库归档模式开启情况</p>
<table>
<tbody>
<tr>
<td width="568">
<p>SQL&gt; archive log list;</p>
<p>Database log mode &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Archive Mode</p>
<p>Automatic archival &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Enabled</p>
<p>Archive destination &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;USE_DB_RECOVERY_FILE_DEST</p>
<p>Oldest online log sequence &nbsp;&nbsp;&nbsp;&nbsp;1618</p>
<p>Next log sequence to archive &nbsp;&nbsp;1620</p>
<p>Current log sequence &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1620</p>
<p>SQL&gt;</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p><img src='./images/9-4.png'>图 9-4 甜点商城查看检查主库检查主库归档模式开启情况</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>9.2.4检查在线日志redolog，确认member和group#，根据在线日志添加standby logfile（以下操作均在CBD下操作）</p>
<table>
<tbody>
<tr>
<td width="568">
<p>SQL&gt; select group#, members, bytes from v$log;</p>
<p>&nbsp;</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;GROUP# &nbsp;&nbsp;&nbsp;MEMBERS &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;BYTES</p>
<p>---------- ---------- ----------</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2 &nbsp;&nbsp;52428800</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1 &nbsp;&nbsp;52428800</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1 &nbsp;&nbsp;52428800</p>
<p>&nbsp;</p>
<p>SQL&gt;</p>
</td>
</tr>
</tbody>
</table>
<p><img src='./images/9-5.png'>图 9-5 甜点商城检查在线日志redolog</p>
<p>添加standby logfile（3+1）：</p>
<table>
<tbody>
<tr>
<td width="568">
<p>ALTER DATABASE ADD STANDBY LOGFILE '/home/app/oracle/oradata/orcl/onlinelog/stdredo01.log' size 50M;</p>
<p>ALTER DATABASE ADD STANDBY LOGFILE '/home/app/oracle/oradata/orcl/onlinelog/stdredo02.log' size 50M;</p>
<p>ALTER DATABASE ADD STANDBY LOGFILE '/home/app/oracle/oradata/orcl/onlinelog/stdredo03.log' size 50M;</p>
<p>ALTER DATABASE ADD STANDBY LOGFILE '/home/app/oracle/oradata/orcl/onlinelog/stdredo04.log' size 50M;</p>
<p>&nbsp;</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p><a name="_Toc13480"></a>9.3.配置两个数据库的网络参数文件tnsname.ora和listener.ora</p>
<p>primary和Standby上的tnsnames.ora相同。</p>
<p><a name="_Toc10426"></a>9.3.1配置tnsnames.ora参数文件</p>
<table>
<tbody>
<tr>
<td width="568">
<p>#primary database</p>
<p>porcl =</p>
<p>(DESCRIPTION =</p>
<p>(ADDRESS_LIST =</p>
<p>(ADDRESS = (PROTOCOL = TCP)(HOST = oracle-one)(PORT = 1521))</p>
<p>(ADDRESS = (PROTOCOL = TCP)(HOST = 10.11.12.1)(PORT = 1521))</p>
<p>)</p>
<p>(CONNECT_DATA =</p>
<p>(SERVICE_NAME = orcl)</p>
<p>)</p>
<p>)</p>
<p>#standby database</p>
<p>sorcl=</p>
<p>(DESCRIPTION =</p>
<p>(ADDRESS = (PROTOCOL = TCP)(HOST = 10.11.12.2)(PORT = 1521))</p>
<p>(CONNECT_DATA =</p>
<p>(SERVER = DEDICATED)</p>
<p>(SERVICE_NAME = orcl)</p>
<p>(UR=A)</p>
<p>)</p>
<p>)</p>
<p>#pluggable database</p>
<p>cdb =</p>
<p>(DESCRIPTION =</p>
<p>(ADDRESS_LIST =</p>
<p>(ADDRESS = (PROTOCOL = TCP)(HOST = oracle-one)(PORT = 1521))</p>
<p>(ADDRESS = (PROTOCOL = TCP)(HOST = 10.11.12.1)(PORT = 1521))</p>
<p>)</p>
<p>(CONNECT_DATA =</p>
<p>(SERVICE_NAME = cdb)</p>
<p>)</p>
<p>)</p>
</td>
</tr>
</tbody>
</table>
<p><a name="_Toc6270"></a>9.3.2配置监听文件</p>
<table>
<tbody>
<tr>
<td width="568">
<p># listener.ora Network Configuration File: /home/app/oracle/product/12.2.0/dbhome_1/network/admin/listener.ora</p>
<p># Generated by Oracle configuration tools.</p>
<p>SID_LIST_LISTENER =</p>
<p>(SID_LIST =</p>
<p>(SID_DESC =</p>
<p>(GLOBAL_DBNAME = orcl)</p>
<p>(ORACLE_HOME = /home/app/oracle/product/12.2.0/dbhome_1)</p>
<p>(SID_NAME = ORCL)</p>
<p>)</p>
<p>)</p>
<p>LISTENER =</p>
<p>(DESCRIPTION_LIST =</p>
<p>(DESCRIPTION =</p>
<p>(ADDRESS = (PROTOCOL = TCP)(HOST = oracle-one)(PORT = 1521))</p>
<p>)</p>
<p>(DESCRIPTION =</p>
<p>(ADDRESS = (PROTOCOL = IPC)(KEY = EXTPROC1521))</p>
<p>)</p>
<p>)</p>
<p>ADR_BASE_LISTENER = /u01/app/oracle</p>
<p>LISTENERD =</p>
<p>(DESCRIPTION_LIST =</p>
<p>(DESCRIPTION =</p>
<p>(ADDRESS = (PROTOCOL = TCP)(HOST = oracle-one)(PORT = 1521))</p>
<p>)</p>
<p>)</p>
</td>
</tr>
</tbody>
</table>
<p><a name="_Toc12407"></a>9.4.配置数据库参数文件</p>
<p>注意：数据库参数文件的调整时注意PDB和CDB的切换运行，否则会报如下错误</p>
<p>9.4.1主库配置完后参数文件：如下（如果是从pfile指定文件启动，启动完成后要创建spfile文件）</p>
<table>
<tbody>
<tr>
<td width="568">
<p>orcl.__data_transfer_cache_size=0</p>
<p>orcl.__db_cache_size=234881024</p>
<p>orcl.__inmemory_ext_roarea=0</p>
<p>orcl.__inmemory_ext_rwarea=0</p>
<p>orcl.__java_pool_size=4194304</p>
<p>orcl.__large_pool_size=8388608</p>
<p>orcl.__oracle_base='/home/app/oracle'#ORACLE_BASE set from environment</p>
<p>orcl.__pga_aggregate_target=272629760</p>
<p>orcl.__sga_target=507510784</p>
<p>orcl.__shared_io_pool_size=20971520</p>
<p>orcl.__shared_pool_size=222298112</p>
<p>orcl.__streams_pool_size=0</p>
<p>*.audit_file_dest='/u01/app/oracle/admin/orcl/adump'</p>
<p>*.audit_trail='db'</p>
<p>*.compatible='12.2.0'</p>
<p>*.control_files='/home/app/oracle/oradata/ORCL/controlfile/o1_mf_dqflr6xp_.ctl','/home/app/oracle/fast_recovery_area/orcl/ORCL/controlfile/o1_mf_dqflr78t_.ctl'</p>
<p>*.db_block_size=8192</p>
<p>*.db_create_file_dest='/home/app/oracle/oradata'</p>
<p>*.db_file_name_convert='/home/app/oracle/oradata/ORCL/datafile/','/u01/app/oracle/oradata/ORCL/datafile/'</p>
<p>*.db_name='orcl'</p>
<p>*.db_recovery_file_dest='/home/app/oracle/fast_recovery_area/orcl'</p>
<p>*.db_recovery_file_dest_size=8016m</p>
<p>*.db_unique_name='porcl'</p>
<p>*.diagnostic_dest='/home/app/oracle'</p>
<p>*.dispatchers='(PROTOCOL=TCP) (SERVICE=orclXDB)'</p>
<p>*.enable_pluggable_database=true</p>
<p>*.fal_client='PORCL'</p>
<p>*.fal_server='SORCL'</p>
<p>*.log_archive_config='DG_CONFIG=(porcl,sorcl)'</p>
<p>*.log_archive_dest_1='location=/home/app/oracle/oradata/arch db_unique_name=porcl'</p>
<p>*.log_archive_dest_2='service=sorcl LGWR ASYNC noaffirm reopen=60 valid_for=(online_logfiles,primary_role) db_unique_name=sorcl'</p>
<p>*.log_archive_dest_state_2='enable'</p>
<p>*.log_file_name_convert='/home/app/oracle/oradata/ORCL/onlinelog/','/home/app/oracle/oradata/ORCL/onlinelog/','/home/app/oracle/fast_recovery_area/orcl/ORCL/onlinelog/','</p>
<p>/home/app/oracle/fast_recovery_area/orcl/ORCL/onlinelog/'</p>
<p>*.memory_target=744m</p>
<p>*.open_cursors=300</p>
<p>*.processes=300</p>
<p>*.remote_login_passwordfile='EXCLUSIVE'</p>
<p>*.service_names='ORCL'</p>
<p>*.standby_file_management='auto'</p>
<p>*.undo_tablespace='UNDOTBS1'</p>
</td>
</tr>
</tbody>
</table>
<p>9.4.2将主库修改后的参数文件传送到备库</p>
<p>9.4.3修改从库数据库参数文件并使用该参数文件从pfile启动</p>
<table>
<tbody>
<tr>
<td width="568">
<p>*.db_unique_name=</p>
<p>*.log_archive_config=</p>
<p>*.log_file_name_convert=</p>
<p>*.db_file_name_convert=</p>
<p>*.log_archive_dest_1=</p>
<p>*.log_archive_dest_2=</p>
<p>*.standby_file_management=</p>
<p>*.fal_server=</p>
<p>*.fal_client=</p>
</td>
</tr>
</tbody>
</table>
<p>9.4.4主库密码文件传送到备库</p>
<table>
<tbody>
<tr>
<td width="568">
<p>[oracle@oracle-pc ~]$ scp orapworcl orcle-one:/dbs/</p>
</td>
</tr>
</tbody>
</table>
<p><a name="_Toc4398"></a>9.5.启动standby database到nomount状态</p>
<p><a name="_Toc6614"></a>9.5.1检查tns连接名是否正常(主备库均需要检查)</p>
<table>
<tbody>
<tr>
<td width="568">
<p>tnsping porcl</p>
<p>tnsping sorcl</p>
<p>lsnrctl</p>
</td>
</tr>
</tbody>
</table>
<p><a name="_Toc20841"></a>9.5.2启动备库</p>
<table>
<tbody>
<tr>
<td width="568">
<p>startup pfile='/home/oracle/standbypfile.ora' nomount</p>
</td>
</tr>
</tbody>
</table>
<p>启动后创建spfile</p>
<table>
<tbody>
<tr>
<td width="568">
<p>create spfile from pfile='/home/oracle/standbypfile.ora'</p>
</td>
</tr>
</tbody>
</table>
<p><a name="_Toc57"></a>参考文献</p>
<p>[1]Oracle 12c 数据库基础教程[M]. 赵卫东、刘永红，于曦.北京：科学出版社，2017.</p>
<p>[2]oracle 12C dataguard搭建. <a href="https://blog.csdn.net/s754520480/article/details/79789771"><u>https://blog.csdn.net/s754520480/article/details/79789771</u></a></p>
<p>[3]Oracle 数据库应用. &nbsp;<a href="https://github.com/zwdcdu/oracle"><u>https://github.com/zwdcdu/oracle</u></a></p>
