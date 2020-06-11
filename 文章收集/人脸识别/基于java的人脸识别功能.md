##### 原博客地址

<https://www.bcdaren.com/554112376329474049/blog_content.html>



基于Java 的人脸识别功能（附源码）博客

- [![img](https://res.bcdaren.com/upload/mainServer/header/2018/09/18/18/10717096457121367.JPG)](https://www.bcdaren.com/358948055862743040/userInfo.html)

  ##### [滴水逆向 等级 N0](https://www.bcdaren.com/358948055862743040/userInfo.html)

  2020-03-09 09:24

   

  #### 引言

  远程在家办公的第N天，快要闲出屁了，今天突然有个小学弟加我VX说要咨询我点技术问题（终于可以装X了）。 看了他的需求描述，大概是要做一个Java web版本的人脸识别功能，然后存储人物的特征，再扫脸比对。可是我不会啊。。。

  不过，作为一个宠粉的暖男，别说有困难就是没困难制造困难也要上，既然人家这么真诚的咨询，说明我还是有被需要的价值，不会那就帮着查查资料吧！没想到还有意外的收获~

  

  

  在这里插入图片描述

  
  看完他的境遇，忽然想起自己当年做毕设时那无助的样子，是何等的相似。每每看到有这样的咨询，能帮的我都尽自己最大努力帮，毕竟都是这么走过来的。

  

  #### 人脸识别SDK

  人脸识别技术是很复杂的，自己用Java手撕一个识别算法有点不切实际，毕竟实力不允许我这么嚣张，还是借助三方的SDK吧！

  找了一圈发现一个免费的人脸识别SDK： ArcSoft:，地址：https://ai.arcsoft.com.cn。

  **官网首页 -> 右上角开发者中心 -> 选择“人脸识别” -> 添加SDK**，会生成APPID、SDK KEY后续会用到，根据需要选择不同的环境（**本文基于windows环境**），然后下载SDK是一个压缩包。

  

  

  在这里插入图片描述

  #### Java项目搭建

  终于在我的苦苦搜寻之下终于，找到一个ArcSoft的Java版本Demo，开源真是一件美好的事情，话不多说开干！

  

  

  在这里插入图片描述

  
  **1、下载demo项目**

  

  github地址：https://github.com/xinzhfiu/ArcSoftFaceDemo，本地搭建数据库，创建表:user_face_info。这个表主要用来存人像特征，其中主要的字段 face_feature 用二进制类型 blob 存放人脸特征。

  ```
  SET NAMES utf8mb4;
  SET FOREIGN_KEY_CHECKS = 0;
  
  -- ----------------------------
  -- Table structure for user_face_info
  -- ----------------------------
  DROP TABLE IF EXISTS `user_face_info`;
  CREATE TABLE `user_face_info` (
    `id` int(11) NOT NULL AUTO_INCREMENT COMMENT '主键',
    `group_id` int(11) DEFAULT NULL COMMENT '分组id',
    `face_id` varchar(31) DEFAULT NULL COMMENT '人脸唯一Id',
    `name` varchar(63) DEFAULT NULL COMMENT '名字',
    `age` int(3) DEFAULT NULL COMMENT '年纪',
    `email` varchar(255) DEFAULT NULL COMMENT '邮箱地址',
    `gender` smallint(1) DEFAULT NULL COMMENT '性别，1=男，2=女',
    `phone_number` varchar(11) DEFAULT NULL COMMENT '电话号码',
    `face_feature` blob COMMENT '人脸特征',
    `create_time` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP COMMENT '创建时间',
    `update_time` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP COMMENT '更新时间',
    `fpath` varchar(255) COMMENT '照片路径',
    PRIMARY KEY (`id`) USING BTREE,
    KEY `GROUP_ID` (`group_id`) USING BTREE
  ) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf8mb4 ROW_FORMAT=DYNAMIC;
  SET FOREIGN_KEY_CHECKS = 1;
  ```

  **2、修改application.properties文件**

  整个项目还是比较完整的，只需改一些配置即可启动，但有几点注意的地方，后边会重点说明。

  config.arcface-sdk.sdk-lib-path： 存放SDK压缩包中的三个.dll文件的路径

  config.arcface-sdk.app-id ： 开发者中心的APPID

  config.arcface-sdk.sdk-key ：开发者中心的SDK Key

  ```
  config.arcface-sdk.sdk-lib-path=d:/arcsoft_lib
  config.arcface-sdk.app-id=8XMHMu71Dmb5UtAEBpPTB1E9ZPNTw2nrvQ5bXxBobUA8
  config.arcface-sdk.sdk-key=BA8TLA9vVwK7G6btJh2A2FCa8ZrC6VWZLNbBBFctCz5R
  
  # druid  本地的数据库地址
  spring.datasource.druid.url=jdbc:mysql://127.0.0.1:3306/xin-master?useUnicode=true&characterEncoding=utf-8&useSSL=false&serverTimezone=UTC
  spring.datasource.druid.username=junkang
  spring.datasource.druid.password=junkang
  ```

  **3、根目录创建lib文件夹**

  在项目根目录创建文件夹 lib,将下载的SDK压缩包中的arcsoft-sdk-face-2.2.0.1.jar放入项目根目录

  

  

  在这里插入图片描述

  **4、引入arcsoft依赖包**

  ```
   <dependency>
        <groupId>com.arcsoft.face</groupId>
        <artifactId>arcsoft-sdk-face</artifactId>
        <version>2.2.0.1</version>
        <scope>system</scope>
        <systemPath>${basedir}/lib/arcsoft-sdk-face-2.2.0.1.jar</systemPath>
  </dependency>
  ```

  pom.xml文件要配置includeSystemScope属性，否则可能会导致arcsoft-sdk-face-2.2.0.1.jar引用不到

  ```
   <build>
          <plugins>
              <plugin>
                  <groupId>org.springframework.boot</groupId>
                  <artifactId>spring-boot-maven-plugin</artifactId>
                  <configuration>
                      <includeSystemScope>true</includeSystemScope>
                      <fork>true</fork>
                  </configuration>
              </plugin>
          </plugins>
      </build>
  ```

  **5、启动项目**

  到此为止配置完成，run Application文件启动

  测试一下：http://127.0.0.1:8089/demo，如下页面即启动成功

  

  

  在这里插入图片描述

  #### 操作

  **1、录入人脸图像**

  页面输入名称，点击摄像头注册调起本地摄像头，提交后将当前图像传入后台，识别提取当前人脸体征，保存至数据库。

  

  

  在这里插入图片描述

  
  **2、人脸对比**

  

  录入完人脸图像后测试一下能否识别成功，提交当前的图像，发现识别成功相似度92%。但是作为程序员对什么事情都要持怀疑的态度，**这结果不是老铁在页面写死的吧？**

  

  

  在这里插入图片描述

  
  为了进一步验证，这回把脸挡住再试一下，发现提示“人脸不匹配”，证明真的有进行比对。

  

  

  在这里插入图片描述

  #### 源码分析

  简单看了一下项目源码，分析一下实现的过程：

  页面和JS一看就是后端程序员写的，不要问我问为什么？懂的自然懂，哈哈哈 ~ ，

  **1、JS调起本地摄像头拍照，上传图片文件字符串**

  ```
      function getMedia() {
          $("#mainDiv").empty();
          let videoComp = " <video id='video' width='500px' height='500px' autoplay='autoplay'></video><canvas id='canvas' width='500px' height='500px'></canvas>";
          $("#mainDiv").append(videoComp);
  
          let constraints = {
              video: {width: 500, height: 500},
              audio: true
          };
          //获得video摄像头区域
          let video = document.getElementById("video");
          //这里介绍新的方法，返回一个 Promise对象
          // 这个Promise对象返回成功后的回调函数带一个 MediaStream 对象作为其参数
          // then()是Promise对象里的方法
          // then()方法是异步执行，当then()前的方法执行完后再执行then()内部的程序
          // 避免数据没有获取到
          let promise = navigator.mediaDevices.getUserMedia(constraints);
          promise.then(function (MediaStream) {
              video.srcObject = MediaStream;
              video.play();
          });
  
          // var t1 = window.setTimeout(function() {
          //     takePhoto();
          // },2000)
      }
  //拍照事件
      function takePhoto() {
          let mainComp = $("#mainDiv");
          if(mainComp.has('video').length)
          {
              let userNameInput = $("#userName").val();
              if(userNameInput == "")
              {
                  alert("姓名不能为空!");
                  return false;
              }
              //获得Canvas对象
              let video = document.getElementById("video");
              let canvas = document.getElementById("canvas");
              let ctx = canvas.getContext('2d');
              ctx.drawImage(video, 0, 0, 500, 500);
              var formData = new FormData();
              var base64File = canvas.toDataURL();
              var userName = $("#userName").val();
              formData.append("file", base64File);
              formData.append("name", userName);
              formData.append("groupId", "101");
              $.ajax({
                  type: "post",
                  url: "/faceAdd",
                  data: formData,
                  contentType: false,
                  processData: false,
                  async: false,
                  success: function (text) {
                      var res = JSON.stringify(text)
                      if (text.code == 0) {
                          alert("注册成功")
                      } else {
                          alert(text.message)
                      }
                  },
                  error: function (error) {
                      alert(JSON.stringify(error))
                  }
              });
          }
          else{
              var formData = new FormData();
              let userName = $("#userName").val();
              formData.append("groupId", "101");
              var file = $("#file0")[0].files[0];
              var reader = new FileReader();
              reader.readAsDataURL(file);
              reader.onload = function () {
              var base64 = reader.result;
              formData.append("file", base64);
              formData.append("name",userName);
                  $.ajax({
                      type: "post",
                      url: "/faceAdd",
                      data: formData,
                      contentType: false,
                      processData: false,
                      async: false,
                      success: function (text) {
                          var res = JSON.stringify(text)
                          if (text.code == 0) {
                              alert("注册成功")
                          } else {
                              alert(text.message)
                          }
                      },
                      error: function (error) {
                          alert(JSON.stringify(error))
                      }
                  });
                  location.reload();
              }
          }
  
      }
  ```

  **2、后台解析图片，提取人像特征**

  后台解析前端传过来的图片，提取人像特征存入数据库，人像特征的提取主要是靠FaceEngine引擎，顺着源码一路看下去，自己才疏学浅实在是没懂具体是个什么样的算法。

  ```
   /*
      人脸添加
       */
      @RequestMapping(value = "/faceAdd", method = RequestMethod.POST)
      @ResponseBody
      public Result<Object> faceAdd(@RequestParam("file") String file, @RequestParam("groupId") Integer groupId, @RequestParam("name") String name) {
  
          try {
  
              //解析图片
              byte[] decode = Base64.decode(base64Process(file));
              ImageInfo imageInfo = ImageFactory.getRGBData(decode);
  
              //人脸特征获取
              byte[] bytes = faceEngineService.extractFaceFeature(imageInfo);
              if (bytes == null) {
                  return Results.newFailedResult(ErrorCodeEnum.NO_FACE_DETECTED);
              }
  
              UserFaceInfo userFaceInfo = new UserFaceInfo();
              userFaceInfo.setName(name);
              userFaceInfo.setGroupId(groupId);
              userFaceInfo.setFaceFeature(bytes);
              userFaceInfo.setFaceId(RandomUtil.randomString(10));
  
              //人脸特征插入到数据库
              userFaceInfoService.insertSelective(userFaceInfo);
  
              logger.info("faceAdd:" + name);
              return Results.newSuccessResult("");
          } catch (Exception e) {
              logger.error("", e);
          }
          return Results.newFailedResult(ErrorCodeEnum.UNKNOWN);
      }
  ```

  **3、人像特征对比**

  人脸识别：将前端传入的图像经过人像特征提取后，和库中已存在的人像信息对比分析

  ```
  /*
      人脸识别
       */
      @RequestMapping(value = "/faceSearch", method = RequestMethod.POST)
      @ResponseBody
      public Result<FaceSearchResDto> faceSearch(String file, Integer groupId) throws Exception {
          byte[] decode = Base64.decode(base64Process(file));
          BufferedImage bufImage = ImageIO.read(new ByteArrayInputStream(decode));
          ImageInfo imageInfo = ImageFactory.bufferedImage2ImageInfo(bufImage);
  
          //人脸特征获取
          byte[] bytes = faceEngineService.extractFaceFeature(imageInfo);
          if (bytes == null) {
              return Results.newFailedResult(ErrorCodeEnum.NO_FACE_DETECTED);
          }
          //人脸比对，获取比对结果
          List<FaceUserInfo> userFaceInfoList = faceEngineService.compareFaceFeature(bytes, groupId);
  
          if (CollectionUtil.isNotEmpty(userFaceInfoList)) {
              FaceUserInfo faceUserInfo = userFaceInfoList.get(0);
              FaceSearchResDto faceSearchResDto = new FaceSearchResDto();
              BeanUtil.copyProperties(faceUserInfo, faceSearchResDto);
              List<ProcessInfo> processInfoList = faceEngineService.process(imageInfo);
              if (CollectionUtil.isNotEmpty(processInfoList)) {
                  //人脸检测
                  List<FaceInfo> faceInfoList = faceEngineService.detectFaces(imageInfo);
                  int left = faceInfoList.get(0).getRect().getLeft();
                  int top = faceInfoList.get(0).getRect().getTop();
                  int width = faceInfoList.get(0).getRect().getRight() - left;
                  int height = faceInfoList.get(0).getRect().getBottom() - top;
  
                  Graphics2D graphics2D = bufImage.createGraphics();
                  graphics2D.setColor(Color.RED);//红色
                  BasicStroke stroke = new BasicStroke(5f);
                  graphics2D.setStroke(stroke);
                  graphics2D.drawRect(left, top, width, height);
                  ByteArrayOutputStream outputStream = new ByteArrayOutputStream();
                  ImageIO.write(bufImage, "jpg", outputStream);
                  byte[] bytes1 = outputStream.toByteArray();
                  faceSearchResDto.setImage("data:image/jpeg;base64," + Base64Utils.encodeToString(bytes1));
                  faceSearchResDto.setAge(processInfoList.get(0).getAge());
                  faceSearchResDto.setGender(processInfoList.get(0).getGender().equals(1) ? "女" : "男");
  
              }
  
              return Results.newSuccessResult(faceSearchResDto);
          }
          return Results.newFailedResult(ErrorCodeEnum.FACE_DOES_NOT_MATCH);
      }
  ```

  整个人脸识别功能的大致流程图如下：

  

  

  在这里插入图片描述

  #### 总结

  整个项目的设计思路比较清晰，难点在于人脸识别引擎 和 前端JS部分代码，其他的功能比较平常。

  源码地址：https://github.com/xinzhfiu/ArcSoftFaceDemo/，有任何技术问题，欢迎随时沟通