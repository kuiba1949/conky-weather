# conky-weather
conky 天气。
可以显示3天内的天气，并能联网自动定位城市。
说明：自动定位只能到城市，但可以手动修改设置，显示更详细的区/县的天气。

conky-weather

* version 2.4.1, 2018-3-11, by Careone


    Conky天气 ( conky-weather ) 最后的设置

  软件包安装完成后，需要做的3件事情：

  1. 以普通用户，运行命令 conky-weather.runonce 一次!
  只需要运行一次即可！

  主要作用：
  * 替换/更新用户的 ~/.conkyrc 配置文件；
  * 添加conky和Conky天气 (conky-weather) 的开机自启动项；
  * 设定为每隔20分钟更新一次conky天气；

  (更详细的说明，请查看 /etc/conky/themes/madness/README.zh_CN 文件)

  2. 在配置文件中，把conky天气的城市数据网页地址，修改为对应的地址：

  配置文件: ~/conky/conky-weather.cfg
  默认数据地址: https://tianqi.moji.com/ （数据来源：墨迹天气）
  默认的城市: 北京

  注：默认的配置文件 ~/conky/conky-weather.cfg 中, 
      有城市数据地址示例和说明，方便参考。

  3. 以普通用户，运行命令 conky-weather-update, 立即更新新城市的天气！

  注：以后每次开机后，或者每隔20分钟，都会自动更新Conky天气！
  (提示：也可以手动运行 conky-weather-update 立即更新天气！)

  -----------

ChangeLog for conky-weather 
coding: utf-8

* version 2.4.1, 2018-3-11, by Careone


	* 托管地址转移到 github 。原来放在 SourceForge, 有时会无法正常下载和上传文件；
	  原项目网址: 
	  https://sourceforge.net/projects/emacslocale/files/conky-weather/
	  
	  新的项目网址:
	  https://github.com/kuiba1949/conky-weather/
	  
	* 授权协议使用BSD三言许可协议。为适应当前协议，移除了部分可能引起争议的文件:

	** 移除了 usr/share/conky-weather/pixmaps/moji-weather/ 目录下的天气图片。
	   图片来自墨迹天气 https://tianqi.moji.com; 
	   
	** 移除了 etc/conky/themes/madness/conkyrc 文件；


* version 2.4, 2018-3-11, by Careone

	* 修复: 天气图片无法显示的缺陷；
	  原因：程序无法自动创建用户目录 $PIC_DIR，即 ~/conky/moji-weather/，
	  另外自动下载天气图片的相关代码有缺陷（见 TAG 374）；
	  临时解决方案：手动创建目录 ~/conky/moji-weather/ 即可；

	* 新选项: --auto  启用 [自动漫游] 模式。即按IP地址定位城市后，
                   再更新天气。默认使用这种模式。
		   	
	* 新选项: --logcity  启用 [城市备份] 功能。如果更新天气时发现城市地址有变更，
          则自动备份新的天气网址到文件 ~/conky/conky-weather.autocity

	* 其它细节微调，代码优化；


* version 2.3, 2018-3-08, by Careone
	
	* 新增选项: --ip2city 
	  根据IP地址，自动定位城市和天气网页地址；
	  定位过程中需要联网，IP地址数据来自 https://ip.cn

	* 其它细节微调，代码优化；


* version 2.2, 2018-3-05, by Careone
	
	* 新增功能: 支持显示天气图片。图片目录位置: 
	 /usr/share/conky-weather/pixmaps/moji-weather/；

	* 新增功能: 支持在conky中显示提醒信息（实际操作即读取文件 ~/conky/todo.txt
	  的内容。最多只显示5行，防止文件行数太多，导致conky其它信息无法正常显示）;
	  
  	* 更新: /usr/local/bin/conky-weather-update ver 2.1 -> 2.2

	** 修复: 某些情况下，无法正常获取“城市/县城”字符数据，以及“明天”和“后天”的
		天气数据无效的缺陷；
	** 代码优化, 能更有效地解析天气数据; 

	** 新增更多选项：
	  --conkyrc 编辑conky配置文件 ~/.conkyrc
	  --city  修改要显示天气的城市的网页地址(即修改配置文件
		  ~/conky/conky-weather.cfg);
	  --todo  可编辑要提醒的文字内容(即修改配置文件 ~/conky/todo.txt)；

	* 更新: etc/etc/conky/themes/madness/conkyrc_mini
  	 (注：本次未更新 etc/etc/conky/themes/madness/conkyrc ) 


* version 2.1, 2018-3-03, by Careone
	
	* 更新: etc/etc/conky/themes/madness/conkyrc_mini

	** 支持显示最三天内的天气（旧版本只显示今天的天气），
	** 同时调整了天气数据的文件保存规则：
	  现统一保存到单一的文件 ~/conky/conky-weather.db , 不再使用以前的多个文件：
	  ~/.feed/feed_city, feed_ls, feed_xls, feed_wd ；
	  
  	* 更新: etc/etc/conky/themes/madness/conkyrc
  	 （更新规则参照上面的 conkyrc_mini）
  	 
  	* 更新: /usr/local/bin/conky-weather-update, 优化代码，并删除了部分过期的代码； 
  	
  	* 更新: /usr/local/bin/conky-weather-add-crontab
  	      和 /usr/local/bin/conky-weather.runonce
  	天气更新频率由原来的1小时，变更为每20分钟更新一次；


* version 2.0, 2018-2-07, by Careone

	* 更新: DEB 格式软件包的源文件 DEBIAN/postinst
	  安装完成后，会弹窗提示进行最后的设置，来修改城市数据、添加自动启动、
	  自动更新天气; 

	* 更新: /etc/conky/themes/madness/conkyrc_mini
	  + 时间显示中，不再显示秒数(即取消了 $time 的 ":%S" 值)；
	  + 更新时间间隔(update_interval)从1秒调整为5秒；

	* 把原 README.zh_CN 分拆为两个文件: ChangeLog.zh_CN 和 README.zh_CN; 

	* 更新: etc/conky/themes/madness/ChangeLog.zh_CN:
	  + 修复了原 Changelog 部分，版本1.1，年份数字2018误写成20118的错误；

	* 更新: usr/local/bin/conky-weather-update 2.0
  	  添加 -w 和其它选项

	* 更新: usr/local/bin/conky-weather-add-crontab 2.0
  	  如果已存在 ~/conky/86conky-weather-update.cron 计划任务示例文件，
  	  则直接使用这个文件，而不再是重新生成文件（取消无意义的文件写入操作）；  	  

