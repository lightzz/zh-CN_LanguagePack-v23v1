将此语言包导入生产环境之前，Aras 建议您创建数据库和代码树的备份。

这些是使用当前简体中文语言包和 zh-cn 语言环境设置计算机的通用说明。
请注意，简体中文语言包的安装适用于大多数用户将运行简体中文 Aras Innovator 的系统。

第 1 步 - 配置设置。
-----------------------------
1) 编辑 SETUP-DEFAULTS.CMD.

您需要定义以下每个变量：

>前四个变量用于创建语言和区域设置以及使用解决方案升级工具进行任何其他 AML 更改。
```
SERVER_URL = 用于连接到 Aras Innovator 的基本 URL
                #示例：默认安装中的 http://localhost/InnovatorServer
                确保 URL 中不包含 /Client http://localhost/InnovatorServer/Client

DATABASE_ID = 这是 Aras Innovator 用于识别 Aras Innovator 数据库的 ID。
                该值可以在 Aras Innovator InnovatorServerConfig.xml 的 DB-connection 标记中找到。 (id="InnovatorSolutions")

INNOVATOR_LOGIN = 这是管理登录名，将用于创建语言和区域设置项以及进行必要的 AML 更改。
                    新安装应该只使用“root”。

INNOVATOR_PASSWORD = 这是管理登录的密码，将用于创建语言和区域设置项以及进行必要的 AML 更改。
                    “root”的默认密码是“innovator”
```

>最后四个变量用于使用语言包管理实用程序导入语言值。
```   
DB_SERVER = 安装 Aras Innovator 数据库的 SQL Server 实例的名称。
            该值可以在 Aras Innovator InnovatorServerConfig.xml 的 DB-connection 标记中找到。 （服务器=“localhost”）

DATABASE_NAME = SQL Server 中 Aras Innovator 数据库的名称。
                该值可以在 Aras Innovator InnovatorServerConfig.xml 的 DB-connection 标记中找到。 （数据库=“InnovatorSolutions”）

SQL_LOGIN = 分配给 SQL Server 中 Aras Innovator 数据库的 innovator 用户的登录名。
            该值可以在 Aras Innovator InnovatorServerConfig.xml 的 DB-connection 标记中找到。 （uid=“innovator”）

SQL_PASSWORD = 分配给 SQL Server 中 Aras Innovator 数据库的 innovator 用户的登录密码。
                该值可以在 Aras Innovator InnovatorServerConfig.xml 的 DB-connection 标记中找到。 (pwd=“innovator”)
```

步骤 2 - 安装客户端 xml 目录。
--------------------------------------------
>将该目录下找到的\Innovator文件夹复制到服务器覆盖Aras Innovator 安装文件夹中的 \Innovator 文件夹。这将在 Aras Innovator 代码树中创建新目录：

```
\OAuthServer\i18n\xml.zc
\Innovator\Client\xml.zc
\Innovator\Client\Solutions\PLM\xml.zc
\Innovator\Client\Modules\aras.innovator.core.EffectivityServices\xml.zc
\Innovator\Client\Modules\aras.innovator.DomainAccessControl\xml.zc
\Innovator\Client\Modules\aras.innovator.ExtendedClassification\xml.zc
\Innovator\Client\Modules\aras.innovator.MacPolicy\xml.zc
\Innovator\Client\Modules\aras.innovator.MassPromote\xml.zc
\Innovator\Client\Modules\aras.innovator.CMF\xml.zc
\Innovator\Client\Modules\aras.innovator.CUI\xml.zc
\Innovator\Client\Modules\aras.innovator.ES\xml.zc
\Innovator\Client\Modules\aras.innovator.Izenda\xml.zc
\Innovator\Client\Modules\aras.innovator.QueryBuilder\xml.zc
\Innovator\Client\Modules\aras.innovator.SSVC\xml.zc
\Innovator\Client\Modules\aras.innovator.TDF\xml.zc
\Innovator\Client\Modules\aras.innovator.TreeGridView\xml.zc
\Innovator\Client\Modules\aras.innovator.Viewers\xml.zc
\Innovator\Client\scripts\CodeEditor\xml.zc
\Innovator\Client\scripts\ReportTool\xml.zc
\Innovator\Client\scripts\SitePreference\xml.zc
```

>系统可能会提示您覆盖多个文件，这是进行更改以正确查看简体中文标签所必需的

步骤 3 - 运行批处理脚本。
------------------------------
1) 001-IMPORT-I18N-CHANGES.BAT

  >此文件将运行简体中文语言项、zh-cn 区域设置项的解决方案导入以及处理 <Surname> <Personal Name>命名格式的几种方法。

2) 003-RESTART-WEB-SERVICE.BAT

  >这将在本地计算机上重新启动万维网发布服务（应该与
   >作为Innovator Server）。

3) 004-IMPORT-CHINESE_SIMP.BAT

  >这将加载简体中文翻译。
  >该脚本将数据库中信息导出到翻译目录 \Chinese_Simplified 中

#关于作者  
zh-CN_LanguagePack的中文翻译是lightzz，中国大陆地区的自由程序员，主要使用Aras平台进行二次开发，也做一些工程、仿真软件的二次开发。本软件完全免费，如果你喜欢本系列，也欢迎赞助。
![收款二维码](https://github.com/lightzz/zh-CN_LanguagePack-v23v1/assets/20766235/0e9c06b6-a086-4c33-bf55-dfb60c64bc53)
