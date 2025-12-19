### 系统介绍

基于SpringBoot和Vue实现的电影院售票系统采用前后端分离的架构方式，前台系统实现了用户注册/登录、首页、电影、活动、搜索、购物车、我的订单、个人设置等功能模块，客服系统实现了影院留言、电话回访、活动安排、信息统计、我的评价、个人设置等功能模块，后台系统实现了影视管理、用户管理、订单管理、员工管理、Api接口等功能模块。

### 技术选型

开发工具：idea2020.3+webstorm2020.3

运行环境：jdk1.8+mysql5.7+nodejs14.21.3+redis5.0.9

服务端技术：springboot+mybatis-plus+data-redis+fastjson

前端技术：html+css+vue+axios+element-ui+echarts

### 成果展示

前台系统->注册/登录 输入图片说明

前台系统->首页 输入图片说明

前台系统->电影 输入图片说明

前台系统->活动 输入图片说明

前台系统->留言 输入图片说明

前台系统->购物车 输入图片说明

前台系统->我的订单 输入图片说明

客服系统->影院留言 输入图片说明

客服系统->电话回访 输入图片说明

客服系统->活动安排 输入图片说明

客服系统->信息统计 输入图片说明

客服系统->我的评价 输入图片说明

后台系统->影视管理 输入图片说明

后台系统->用户管理 输入图片说明

后台系统->订单管理 输入图片说明

后台系统->员工管理 输入图片说明

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

输入图片说明

4、项目结构展示

输入图片说明

5、运行步骤

1）创建数据库、导入sql脚本

2）修改application.yml中的数据库配置文件，启动服务端

3）分别在vue-app、vue-worker以及vue-admin目录下打开cmd，执行npm install下载依赖

4）下载完毕后启动前端npm run serve，访问端口

### 获取方式(可远程调试)

访问链接(在浏览器中手动输入下图中的地址)：

输入图片说明

若资源获取失败，可添加happy35596339(vx)或1204901965(qq)进行交流
