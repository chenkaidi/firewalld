### 开启防火墙
```
systemctl start firewalld.service
```

#### 防火墙开机启动
```
systemctl enable firewalld.service
```

#### 关闭防火墙
```
systemctl stop firewalld.service
```

##### 查看防火墙状态
```
firewall-cmd --state
```

##### 查看现有的规则
```
iptables -nL
firewall-cmd --zone=public --list-ports
```

##### 添加单个端口
```
firewall-cmd --permanent --zone=public --add-port=3306/tcp
```

##### 添加多个端口
```
firewall-cmd --permanent --zone=public --add-port=8080-8083/tcp
```

##### 删除某个端口
```
firewall-cmd --permanent --zone=public --remove-port=3306/tcp
```

##### 针对某个IP开放端口
```
firewall-cmd --permanent --add-rich-rule="rule family="ipv4" source address="192.168.142.166" port protocol="tcp" port="3306" accept"
```

##### 删除某个IP
```
firewall-cmd --permanent --remove-rich-rule="rule family="ipv4" source address="192.168.1.51" accept"
```

##### 针对一个ip段访问
```
firewall-cmd --permanent --add-rich-rule="rule family="ipv4" source address="192.168.0.0/16" accept"
firewall-cmd --permanent --add-rich-rule="rule family="ipv4" source address="192.168.1.0/24" port protocol="tcp" port="9200" accept"
```

##### 开放所以内网ip访问
```
firewall-cmd --permanent --add-rich-rule="rule family="ipv4" source address="10.0.0.0/8" accept"
firewall-cmd --permanent --add-rich-rule="rule family="ipv4" source address="172.16.0.0/12" accept"
firewall-cmd --permanent --add-rich-rule="rule family="ipv4" source address="192.168.0.0/16" accept"
```

# reload 重载
```
firewall-cmd --reload
```
