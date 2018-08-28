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

````

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

