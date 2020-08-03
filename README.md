# nginx-proxy-ldap-manager
Fork [nginx-proxy-manager](https://github.com/jc21/nginx-proxy-manager) and  add [LDAP module](https://github.com/kvspb/nginx-auth-ldap)
nginx-proxy-ldap:https://gitlab.com/shuhanghang/docker-alpine-nginx-base
nginx-proxy-ldap-manager:https://gitlab.com/shuhanghang/nginx-proxy-ldap-manager
## 1.Install

```shell
docker-compose up -d
```

## 2.Example configuration

vim  nginx.conf

```shell
        # Ldap group:Nginx1
      	 ldap_server ad_1 {                                                                            
         url "ldap://172.16.10.10:3268/DC=test,DC=com?sAMAccountName?sub?(objectClass=person)";     
         binddn "test\\admin";                                                                   
         binddn_passwd "password";                                                                 
         group_attribute member;                                                                      
         group_attribute_is_dn on;                                                                    
         satisfy any;                                                                                 
         require group "CN=Nginx1,OU=Nginx-proxy,DC=test,DC=com";                                      
         }  
		 
	 # Ldap group:Nginx2
	 ldap_server ad_2 {                                                                            
         url "ldap://172.16.10.10:3268/DC=test,DC=io?sAMAccountName?sub?(objectClass=person)";     
         binddn "test\\admin";                                                                   
         binddn_passwd "password";                                                                 
         group_attribute member;                                                                      
         group_attribute_is_dn on;                                                                    
         satisfy any;                                                                                 
         require group "CN=Nginx2,OU=Nginx-proxy,DC=test,DC=com";                                     
         }  
```

### 3.Login 

Default Administrator User

```shell
Email:    admin@example.com
Password: changeme
```

### 4.Edit Proxy Host

![UAEhB6.png](https://s1.ax1x.com/2020/07/07/UAEhB6.png)
