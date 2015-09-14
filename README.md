# goini<br/>
这是一个golang读取ini配置文件的工具，<br/>
<br/>
#描述<br/>
<br/>
使用goini更简单的读取go的ini配置文件以及根据特定格式的各种配置文件。<br/>
<br/>
#安装方法<br/>
<br/>
gp get github.com/widuu/goini<br/>
#使用方法<br/>
<br/>
#ini配置文件格式样列<br/>
[database]<br/>
username = root<br/>
password = password<br/>
hostname = localhost<br/>
<br/>
[admin]<br/>
username = root<br/>
password = password<br/>
<br/>
[nihao]<br/>
username = root<br/>
password = password<br/>
#初始化<br/>
conf := goini.SetConfig("./conf/conf.ini") //goini.SetConfig(filepath) 其中filepath是你ini 配置文件的所在位置<br/>
#获取单个配置信息<br/>
username := conf.GetValue("database", "username") //database是你的[section]，username是你要获取值的key名称<br/>
fmt.Println(username) //root<br/>
#删除一个配置信息<br/>
conf.DeleteValue("database", "username")    //username 是你删除的key<br/>
username = conf.GetValue("database", "username")<br/>
if len(username) == 0 {<br/>
    fmt.Println("username is not exists") //this stdout username is not exists<br/>
}<br/>
#添加一个配置信息<br/>
conf.SetValue("database", "username", "widuu")<br/>
username = conf.GetValue("database", "username")<br/>
fmt.Println(username) //widuu 添加配置信息如果存在[section]则添加或者修改对应的值，如果不存在则添加section<br/>
#获取所有配置信息<br/>
conf.ReadList() //返回[]map[string]map[string]string的格式 即setion=>key->value<br/>
goini<br/>
#About<br/>
<br/>
使用goini更简单的读取go的ini配置文件以及根据特定格式的各种配置文件。<br/>
<br/>
#install<br/>
<br/>
go get github.com/nikeyhi/goini<br/>
#use example<br/>
<br/>
conf.ini<br/>
[database]<br/>
username = root<br/>
password = password<br/>
hostname = localhost<br/>
<br/>
[admin]<br/>
username = root<br/>
password = password<br/>
<br/>
[nihao]<br/>
username = root<br/>
password = password<br/>
<br/>
###initialize<br/>
conf := goini.SetConfig("./conf/conf.ini") //goini.SetConfig(filepath) filepath = directory+file<br/>
###To obtain a single configuration information<br/>
username := conf.GetValue("database", "username") //username is your key you want get the value<br/>
fmt.Println(username) //root<br/>
###To delete a configuration information<br/>
conf.DeleteValue("database", "username")    //username is your delete the key<br/>
username = conf.GetValue("database", "username")<br/>
if len(username) == 0 {<br/>
    fmt.Println("username is not exists") //this stdout username is not exists<br/>
}<br/>
###Add a configuration information<br/>
conf.SetValue("database", "username", "widuu")<br/>
username = conf.GetValue("database", "username")<br/>
fmt.Println(username) //widuu Adding/section configuration information if there is to add or modify the value of the corresponding, if there is no add section<br/>
###Get all the configuration information<br/>
conf.ReadList() //return []map[string]map[string]string  example:setion=>key->value<br/>
