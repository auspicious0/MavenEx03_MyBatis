# MavenEx03_MyBatis
## 0.	목표

maven과 mybatis를 활용하여 db에 접근해 암복호화를 수행하고자 한다. 


특히 이전 프로젝트와는 달리 maven을 사용했을 때의 차이점을 주목해 보고자한다.

## 1.	자바 및 xml 코드와 그에 대한 설명


[이전 프로젝트 코드 설명](https://github.com/auspicious0/connect_mybatis_db)

## 2.	maven pom.xml 코드

```
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>

  <groupId>org.al</groupId>
  <artifactId>test</artifactId>
  <version>0.0.1-SNAPSHOT</version>
  <packaging>jar</packaging>

  <name>test</name>
  <url>http://maven.apache.org</url>

  <properties>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
  </properties>

  <dependencies>
    <dependency>
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <version>3.8.1</version>
      <scope>test</scope>
    </dependency>
    <dependency>
    	<groupId>ap-smart-api</groupId>
    	<artifactId>ap-smart-api</artifactId>
    	<version>3.1.4.34</version>
	</dependency>	

	<dependency>
	    <groupId>mariadb-java-client</groupId>
	    <artifactId>mariadb-java-client</artifactId>
	    <version>3.3.2</version>
	</dependency>
	
	<dependency>
	    <groupId>mybatis</groupId>
	    <artifactId>mybatis</artifactId>
	    <version>3.5.15</version>
	</dependency>
	<dependency>
	    <groupId>xdsp</groupId>
	    <artifactId>xdsp-jni</artifactId>
	    <version>2.1</version>
	</dependency>
  </dependencies>
  <build>
	<resources>
  <resource>
    <directory>src/test/resources</directory>
  </resource>
</resources>
  </build>
  
</project>
```

## 3.	코드 설명


maven은 pom.xml을 통해 library를 추가할 수 있다. 


이전에는 lib라는 폴더를 만들어서 수동으로 library를 등록했다면

위와 같이 pom.xml에 작성한 후 library를 작성한 폴더에 위치시키면 자동으로 maven dependencies로 추가된다. 

아래 xdsp의 예를 통해 이해해보자.


```
<dependency>
	    <groupId>xdsp</groupId>
	    <artifactId>xdsp-jni</artifactId>
	    <version>2.1</version>
	</dependency>
```

xdsp는에 관한 내용을 작성한 후 저장한다면 아래와 같이 폴더가 생성된다.

![image](https://github.com/auspicious0/MavenEx03_MyBatis/assets/108572025/4ea6e787-19ad-4319-ad9f-2ed73a71abc5)

 
다음과 같이 해당 폴더에 jar파일을 위치시킨 후 

![image](https://github.com/auspicious0/MavenEx03_MyBatis/assets/108572025/8b712056-f903-469a-b72a-6235aa914b26)


 
eclipse로 넘어와 alt f5를 눌러 maven project를 최신화 해준다.


![image](https://github.com/auspicious0/MavenEx03_MyBatis/assets/108572025/57c528c9-997e-4004-bcd7-0f9922fafff7)

 
그렇다면 다음과 같이 Maven Dependencies에 해당 라이브러리가 추가된 것을 확인할 수 있다.

![image](https://github.com/auspicious0/MavenEx03_MyBatis/assets/108572025/67960ef6-4202-49b1-a790-fff25632f4b3)
 

또한 해당 코드의 다음 부분을 살펴보자
<build>
	<resources>
  <resource>
    <directory>src/test/resources</directory>
  </resource>
</resources>
  </build>

위의 부분은 build시 src/test/resources 폴더를 classpath로 추가하는 부분이다. 


추가하는 이유는 이 부분에 xml 코드가 있기 때문이다. 



## 4.	실행 결과


 ![image](https://github.com/auspicious0/MavenEx03_MyBatis/assets/108572025/27df8b85-f72f-4c1b-9e5b-db25b6486b4c)

