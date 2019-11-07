//获取所有用户信息

http://localhost:3000/users

//获取id：1的用户信息

http://localhost:3000/users/1

//获取所有公司的信息

http://localhost:3000/companies

//获取所有公司id:1的信息

http://localhost:3000/companies/1

//获取公司id：1的用户信息

http://localhost:3000/companies/1/users

//获取公司名字

http://localhost:3000/companies?name=Microsoft

//获取公司的信息（&根据多个名字）

http://localhost:3000/companies?name=Microsoft&name=Apple

//获取公司页数（并且进行限制）

http://localhost:3000/companies?_page=1&_limit=2

//升序排序

http://localhost:3000/companies?_sort=name&_order=asc

//获取到年龄为30及30以上的

http://localhost:3000/users?age_gte=30

//获取年龄30以上到40之间的

http://localhost:3000/users?age_gte=30&age_lte=40

//获取根据字母进行用户信息搜索

http://localhost:3000/users?q=e