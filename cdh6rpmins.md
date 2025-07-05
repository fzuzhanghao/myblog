
# 服务端安装
安装依赖包，非内网情况直接yum安装
![所需依赖包](https://i-blog.csdnimg.cn/blog_migrate/8ab2563cd577e9f8ee9254049e07f5bb.jpeg)
## vi /etc/krb5.conf

```bash
[libdefaults]
default_realm = XXX.COM
dns_lookup_kdc = false
dns_lookup_realm = false
ticket_lifetime = 86400
renew_lifetime = 604800
forwardable = true
default_tgs_enctypes = rc4-hmac
default_tkt_enctypes = rc4-hmac
permitted_enctypes = rc4-hmac
udp_preference_limit = 1
kdc_timeout = 3000
[realms]
FUNO.COM = {
kdc = hadoop5
admin_server = hadoop5
}
[domain_realm]
hadoop1 = XXX.COM
hadoop5 = XXX.COM
```

## vi /var/kerberos/krb5kdc/kadm5.acl

```bash
*/admin@XXX.COM     *
*/hadoop5@XXX.COM     *
```


## vi  /var/kerberos/krb5kdc/kdc.conf

```bash
[kdcdefaults]
 kdc_ports = 88
 kdc_tcp_ports = 88

[realms]
 XXX.COM = {
  #master_key_type = aes256-cts
  max_renewable_life= 7d 0h 0m 0s
  acl_file = /var/kerberos/krb5kdc/kadm5.acl
  dict_file = /usr/share/dict/words
  admin_keytab = /var/kerberos/krb5kdc/kadm5.keytab
  supported_enctypes = aes256-cts:normal aes128-cts:normal des3-hmac-sha1:normal arcfour-hmac:normal camellia256-cts:normal camellia128-cts:normal des-hmac-sha1:normal des-cbc-md5:normal des-cbc-crc:normal
 }
```

##  建库

```bash
kdb5_util create –r XXX.COM –s
```

## 建立用户体系

```bash
kadmin.local
```

```bash
addprinc admin/admin@FUNO.COM 
```

```bash
systemctl start krb5kdc
systemctl start kadmin
```

# 客户端安装
将安装包拷贝到各个客户节点
```bash
scp * root@xxx:/home/bigdata/
```

```bash
Ssh xxxx
cd /home/bigdata/
rpm -ivh krb5-libs-1.15.1-51.el7_9.x86_64.rpm
rpm -ivh krb5-workstation-1.15.1-50.el7.x86_64.rpm
```


复制配置文件到各个客户端节点

```bash
scp /etc/krb5.conf root@hadoop4:/etc/
 
```

## CDH启用kerberos
 ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/5738e9971abb52a887173c1dabd2923a.png)

 
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/d614b441d8280a3343111803b835308d.png)

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/0219fd4046ad0eb015cf016fdbe87987.png)


![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/2b193a331214a14d5df8c42a0d8f1e6e.png)


# 代码使用
在使用过程中hbase碰到比较大问题，
基础环境为flinx+hbase shade client 2.0
由于配置要求hbase.regionserver.kerberos.principal必填，结果发现配置hbase/node1@TEST.COM会导致node2写入无权限，配置hbase/node2@TEST.COM会导致node3写入无权限，principal又不支持配置多个，经过查阅官方文档，将host配置改为"_HOST"即可。
hbase/_HOST@TEST.COM
