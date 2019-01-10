# JQuery操作table的一些实现

````js

<!DOCTYPE HTML>  
<html>  
<head>  
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">  
<title>moban</title>  
<script src="http://www.w3school.com.cn/jquery/jquery.js"></script>  
<script type="text/javascript">  
    function  showzhi(obj){
	// 获取table tr的td列表   
    	var x = $(obj).parent().parent().find("td");  
	// 获取td中select的默认选中值
    	var y = x.eq(2).find("select").val();
	// 清空td中select的下拉框值
	x.eq(2).find("select").empty();
	// 添加td中select下拉框的值
	x.eq(2).find("select").append("<option value='223'>Text-1</option>");
	x.eq(2).find("select").append("<option value='23213'>Text-2</option>");
	x.eq(2).find("select").append("<option value='12323'>Text-3</option>");
	x.eq(2).find("select").append("<option value='232323'>Text-4</option>");
	// 设置td中select下拉框的默认选中值
	x.eq(2).find("select").val('12323');	

	alert(y);
    };  
</script>  
</head>  

<body>  
	<table width="80%" border="1">  
		<tr>  
			<td>111</td>  
			<td>aaa</td>  
			<td>
				<select>
					<option value="1">测试仪</option>	
					<option value="11">测试仪1</option>			
				</select>			
			</td>  
			<td><a onclick="showzhi(this)">保存</a></td>  
		</tr>  
		<tr>  
			<td>222</td>  
			<td>bbb</td>  
			<td>
				<select>
					<option value="1">测试仪</option>
					<option value="12" selected>测试仪2</option>				
				</select>
			</td>  
			<td><a onclick="showzhi(this)">保存</a></td>  
		</tr>  
			<tr>  
			<td>333</td>  
			<td>ccc</td>  
			<td>
				<select>
					<option value="1">测试仪</option>	
					<option value="13" selected>测试仪3</option>			
				</select>			
			</td>  
			<td><a onclick="showzhi(this)">保存</a></td>  
		</tr>  
	</table>  
</body>  
</html>  

````

````html

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">

<head>
    <meta http-equiv="Content-Type" content="text/html;charset=utf-8" />
    <title>测试DIV+CSS</title>
    <style type="text/css">
        .left_size {
            display: inline-block;
            background-color: bisque;
            width: 130px;
            margin: 0 auto;
        }
        
        .center {
            display: inline-block;
        }
        
        .right_side {
            display: inline-block;
            background-color: floralwhite;
            width: 130px;
            margin: 0 auto;
        }
        
        a {
            width: 70px;
            display: block;
            overflow: hidden;
            /*注意不要写在最后了*/
            white-space: nowrap;
            -o-text-overflow: ellipsis;
            text-overflow: ellipsis;
        }
    </style>
</head>

<body>
    <div style="width: 300px;background-color:white;margin: 0 auto;">
        <div style="width: 300px;background-color: azure; text-align: center;margin-top: 1px;">
            <div class="left_size">
                <a>测试横排左侧</a>
            </div>
            <div class="center">
                |
            </div>
            <div class="right_side">
                <a>测试横排右侧</a>
            </div>
        </div>

        <div style="width: 300px;background-color:honeydew;text-align: center;margin-top: 1px;">
            <div class="left_size">
                <a>横排左侧</a>
            </div>
            <div class="center">
                |
            </div>
            <div class="right_side">
                <a>
                    横排右侧
                </a>
            </div>
        </div>
        <div style="width: 300px;background-color:honeydew;text-align: center;margin-top: 1px;">
            <div class="left_size">
                <a>横排左侧</a>
            </div>

        </div>
    </div>
</body>

</html>


````
````
<project xmlns="http://maven.apache.org/POM/4.0.0" 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>

	<groupId>com.*</groupId>
	<artifactId>*</artifactId>
	<version>1.0.0</version>
	<packaging>war</packaging>
	<name>*</name>

	<properties>
		<maven.build.timestamp.format>yyyyMMddHHmmss</maven.build.timestamp.format>
		<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
		<project.reporting.outputEncoding>UTF-8</project.reporting.outputEncoding>
	</properties>

    <profiles>
        <profile>
            <id>dev</id>
            <properties>
                <env>dev</env>
            </properties>
            <activation>
                <activeByDefault>true</activeByDefault>
            </activation>
        </profile>
        <profile>
            <id>prod</id>
            <properties>
                <env>prod</env>
            </properties>
        </profile>
    </profiles>

	<build>
		<!-- 打包的名字 -->
		<finalName>${project.artifactId}</finalName>
		<!-- 工程路径结构设置 -->
		<sourceDirectory>src/main/java</sourceDirectory>
		<testSourceDirectory>src/test/java</testSourceDirectory>
		<outputDirectory>target/classes</outputDirectory>
		<testOutputDirectory>target/test-classes</testOutputDirectory>

		<resources>
			<resource><!--此处的设置是打包的时候排除不相关的目录-->
                <directory>src/main/resources/differ</directory><!--此处设置为上面在resource目录下创建的文件夹-->
                <excludes>
                    <exclude>dev/*</exclude>
                    <exclude>prod/*</exclude>
                </excludes>
                <filtering>true</filtering><!--开启过滤器，此处不能忽略！-->
            </resource>
            <resource>
                <directory>src/main/resources/common</directory>
            </resource>
            <resource><!--此处设置是配置相应配置文件夹的路径-->
                <directory>src/main/resources/differ/${env}</directory>
            </resource>
		</resources>

		<plugins>
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-resources-plugin</artifactId>
				<version>2.5</version>
				<configuration>
					<useDefaultDelimiters>false</useDefaultDelimiters>
					<delimiters>
						<delimiter>$(*)</delimiter>
					</delimiters>
					<encoding>UTF-8</encoding>
				</configuration>
			</plugin>

			<plugin>
				<groupId>org.mortbay.jetty</groupId>
				<artifactId>jetty-maven-plugin</artifactId>
				<version>8.1.16.v20140903</version>
				<configuration>
					<scanIntervalSeconds>10</scanIntervalSeconds>
					<webApp>
						<contextPath>/</contextPath>
					</webApp>
					<connectors>
						<connector implementation="org.eclipse.jetty.server.nio.SelectChannelConnector">
							<port>8089</port>
							<maxIdleTime>60000</maxIdleTime>
						</connector>
					</connectors>
				</configuration>
			</plugin>

			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-compiler-plugin</artifactId>
				<version>3.6.0</version>
				<configuration>
					<source>1.8</source>
					<target>1.8</target>
					<encoding>UTF-8</encoding>
					<compilerArguments>
						<verbose />
						<bootclasspath>${java.home}/lib/rt.jar${path.separator}${java.home}/lib/jce.jar</bootclasspath>
					</compilerArguments>
				</configuration>
			</plugin>
			<!-- 复制依赖到指定目录下 -->
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-dependency-plugin</artifactId>
				<version>2.8</version>
				<executions>
					<execution>
						<id>copy</id>
						<phase>initialize</phase>
						<goals>
							<goal>copy</goal>
						</goals>
						<configuration>
							<artifactItems>
								<artifactItem>
									<groupId>com.google.zxing</groupId>
									<artifactId>core</artifactId>
									<type>jar</type>
									<overWrite>true</overWrite>
								</artifactItem>
							</artifactItems>
							<outputDirectory>./src/main/webapp/WEB-INF/lib/</outputDirectory>
			                <overWriteReleases>false</overWriteReleases>
			                <overWriteSnapshots>false</overWriteSnapshots>
			                <overWriteIfNewer>true</overWriteIfNewer>
						</configuration>
					</execution>
				</executions>
			</plugin>	
		</plugins>
	</build>
	
</project>
````
