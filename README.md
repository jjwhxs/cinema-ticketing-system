### 系统介绍

基于SpringBoot和Vue实现的电影院售票系统采用前后端分离的架构方式，前台系统实现了用户注册/登录、首页、电影、活动、搜索、购物车、我的订单、个人设置等功能模块，客服系统实现了影院留言、电话回访、活动安排、信息统计、我的评价、个人设置等功能模块，后台系统实现了影视管理、用户管理、订单管理、员工管理、Api接口等功能模块。

### 技术选型

开发工具：idea2020.3+webstorm2020.3

运行环境：jdk1.8+mysql5.7+nodejs14.21.3+redis5.0.9

服务端技术：springboot+mybatis-plus+data-redis+fastjson

前端技术：html+css+vue+axios+element-ui+echarts

### 成果展示

前台系统->注册/登录
<img width="1899" height="1036" alt="前台系统-注册登录" src="https://github.com/user-attachments/assets/72a8b7b4-7a3a-41c8-bdef-e844aa23178f" />

前台系统->首页
<img width="1879" height="1031" alt="前台系统-首页" src="https://github.com/user-attachments/assets/0a2a8c87-cecf-4bb3-8854-5dacdb1af66f" />

前台系统->电影
<img width="1881" height="1031" alt="前台系统-电影" src="https://github.com/user-attachments/assets/6abafcca-beae-43a8-aa2c-5ef4bcdad717" />

前台系统->活动
<img width="1899" height="1031" alt="前台系统-活动" src="https://github.com/user-attachments/assets/03c3027a-8476-459f-b857-6f9f4ac8d533" />

前台系统->留言
<img width="1877" height="767" alt="前台系统-留言" src="https://github.com/user-attachments/assets/f4791c70-2016-47d2-bbc3-fe73c95439bc" />

前台系统->购物车
<img width="1882" height="1031" alt="前台系统-购物车" src="https://github.com/user-attachments/assets/93297e3c-b390-4d16-97cf-9842daeb59cb" />

前台系统->我的订单
<img width="1884" height="1035" alt="前台系统-我的订单" src="https://github.com/user-attachments/assets/a369f2d1-cd0c-4e4d-93c8-70cb811aadb3" />

客服系统->影院留言
<img width="1896" height="1034" alt="客服系统-影院留言" src="https://github.com/user-attachments/assets/53d54c23-02c8-41c8-9808-2a07fc39c850" />

客服系统->电话回访
<img width="1899" height="1024" alt="客服系统-电话回访" src="https://github.com/user-attachments/assets/00f3e8e0-138e-4eee-b113-3507b0741fbd" />

客服系统->活动安排
<img width="1901" height="1032" alt="客服系统-活动安排" src="https://github.com/user-attachments/assets/708a8c99-7035-4718-bd9d-bf2ef1d874ae" />

客服系统->信息统计
<img width="1897" height="1031" alt="客服系统-信息统计" src="https://github.com/user-attachments/assets/ed415c05-392b-4e75-bec4-5a3c94d245f5" />

客服系统->我的评价
<img width="1897" height="1032" alt="客服系统-我的评价" src="https://github.com/user-attachments/assets/f0b224d9-9e4a-4dd3-abdc-ed4218bf362c" />

后台系统->影视管理
<img width="1875" height="1035" alt="后台系统-影视管理" src="https://github.com/user-attachments/assets/6088869e-4eb0-49f1-98b6-79b7c990a930" />

后台系统->用户管理
<img width="1897" height="1030" alt="后台系统-用户管理" src="https://github.com/user-attachments/assets/b0ee319a-a5c6-48fd-b7a0-da057dccb24b" />

后台系统->订单管理
<img width="1896" height="1029" alt="后台系统-订单管理" src="https://github.com/user-attachments/assets/6bc319a4-3d93-4a0a-9d84-4feae3871aeb" />

后台系统->员工管理
<img width="1879" height="1031" alt="后台系统-员工管理" src="https://github.com/user-attachments/assets/99e81409-50c9-4a6c-85ee-8d231404aafb" />

### 源码展示

@RestController

@Api(tags = "电影接口")

@RequestMapping("/api/film")

public class FilmController {

@Resource

private FilmService filmService;

@PostMapping("")

@ApiOperation(value = "保存电影")

public void save(@RequestBody Film film) {

    filmService.save(film);
    
}

@GetMapping("")

@ApiOperation("列出所有电影")

public List<Film> list(String region, String type) {

    if (region != null && type != null) {
        return filmService.findByRegionAndType(region, type);
    }
    return filmService.findAll();
    
}

@GetMapping("/hot/{limit}")

@ApiOperation("获取热榜电影")

public List<Film> listHots(@PathVariable Integer limit) {

    return filmService.findHots(limit);
    
}

@GetMapping("/name/{name}")

@ApiOperation("搜索电影")

public List<Film> search(@PathVariable String name) {

    return filmService.findLikeName(name);
    
}

@GetMapping("/{id}")

@ApiOperation(value = "根据id查找电影")

public Film findById(@PathVariable String id) {

    return filmService.findById(id);
    
}

@PutMapping("")

@ApiOperation(value = "更新电影")

public void update(@RequestBody Film film) {

    filmService.update(film);
    
}

@DeleteMapping("/{id}")

@ApiOperation(value = "根据id删除电影")

public void deleteById(@PathVariable String id) {

    filmService.deleteById(id);
    
}

}

### 账号地址及其它说明

1、地址说明

前台系统：localhost:8080

客服系统：localhost:8081

后台系统：localhost:8082

2、账号说明

用户：zhazha/123456

客服：manman/123456

管理员：@admin/123456

3、目录结构展示

<img width="984" height="171" alt="目录结构展示" src="https://github.com/user-attachments/assets/0126f4ec-d57b-4ec8-9a61-3d53e190d40f" />

4、项目结构展示

<img width="1761" height="805" alt="项目结构展示" src="https://github.com/user-attachments/assets/c4ae5b61-de6b-42bd-8572-f257aed51abd" />

5、运行步骤

1）创建数据库、导入sql脚本

2）修改application.yml中的数据库配置文件，启动服务端

3）分别在vue-app、vue-worker以及vue-admin目录下打开cmd，执行npm install下载依赖

4）下载完毕后启动前端npm run serve，访问端口

### 获取方式(可远程调试)

访问链接(在浏览器中手动输入下图中的地址)：

<img width="1115" height="121" alt="链接" src="https://github.com/user-attachments/assets/0995ab6c-6d42-4d40-a4ba-07962fcb5c87" />

若资源获取失败，可添加happy35596339(vx)或2061772307(qq)进行交流
