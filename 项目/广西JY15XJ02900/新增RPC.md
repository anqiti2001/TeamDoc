#   jsp
*   位置 `webapp/business/commonJSP/`
*   unemployedInclud.jsp 失业公用页面嵌入页面查询jsp
*   unemployedPopWin.jsp 失业公用页面，弹出查询jsp
*   养老参照失业的弄两个一样的jsp，叫pensionInclud.jsp,pensionPopWin.jsp
*   jsp中失业时间ajc090改为离退休时间aic162
*   jsp中失业原因ajc093改为离退休类别aic161
*   jsp中去掉ajc097、ajc098、ajc099

#   js
*   位置 `webapp/business/commonJS/`
*   参照unemployedComm.js新建一个pensionComm.js
*   js中unemployed替换为pension
*   失业时间ajc090改为离退休时间aic162
*   失业原因ajc093改为离退休类别aic161
*   去掉ajc097、ajc098、ajc099

#   action
*   位置 `benefit_c/com/yinhai/benefit/suggest/action/`
*   参照UnemployedSuggestAction新建一个PensionSuggestAction
*   struts配置可直接写在此文件中： `benefit_c/com/yinhai/benefit/resource/struts/struts-unemployedSuggest.xml`

#   service
*   位置 `benefit_c/com/yinhai/benefit/suggest/service/`
*   impl位置 `benefit_c/com/yinhai/benefit/suggest/service/impl/`
*   参照UnemployedSuggestService、UnemployedSuggestService新建养老的PensionSuggestService、PensionSuggestServiceImpl、
*   配置文件写入： `benefit_c/com/yinhai/benefit/resource/spring-benefit_c.xml`

#   查询sql
*   在benefitRPCDomain中新增查询退休人员基本信息的方法，可参照getUnemployedInfo、与getUnemployedInfoForWin这两个方法
*   sqlmap位置 `benefit_s/com/yinhai/benefit/RPC/sqlmap/sqlmap-benefitRPC.xml`,在此xml中新增两条sql：
```xml
<!-- 读取退休信息  -->
   <select id="getRetireInfo" parameterClass="java.util.HashMap" resultClass="java.util.HashMap">
        SELECT 
               '''' ||
               extractValue(COLUMN_VALUE, '/row/aac001') || '''' || ',''' ||  <!--个人编号-->
               extractValue(COLUMN_VALUE, '/row/aac002') || '''' || ',''' ||  <!--身份证号-->
               extractValue(COLUMN_VALUE, '/row/aac003') || '''' || ',''' ||  <!--姓名-->
               extractValue(COLUMN_VALUE, '/row/aab001') || '''' || ',''' ||  <!--单位编号-->
               extractValue(COLUMN_VALUE, '/row/aae044') || '''' || ',''' ||  <!--单位名称-->
               extractValue(COLUMN_VALUE, '/row/aab019') || '''' || ',''' ||  <!--单位类型-->
               extractValue(COLUMN_VALUE, '/row/aac004') || '''' || ',''' ||  <!--性别-->
               extractValue(COLUMN_VALUE, '/row/aac005') || '''' || ',''' ||  <!--民族-->
               extractValue(COLUMN_VALUE, '/row/aac006') || '''' || ',''' ||  <!--出生日期-->
               extractValue(COLUMN_VALUE, '/row/aae116') || '''' || ',''' ||  <!--发放状态-->
               extractValue(COLUMN_VALUE, '/row/aic161') || '''' || ',''' ||  <!--离退休类别-->
               extractValue(COLUMN_VALUE, '/row/aic162') || '''' || ',''' ||  <!--离退休时间-->
               extractValue(COLUMN_VALUE, '/row/aae210') || '''' || ',''' ||  <!--待遇享受开始年月-->
               extractValue(COLUMN_VALUE, '/row/yac001') || '''' || ',''' ||  <!--个人最大发放期-->
               extractValue(COLUMN_VALUE, '/row/aaz257') || '''' || ',''' ||  <!--享受定期待遇人员ID-->
               extractValue(COLUMN_VALUE, '/row/aaz157') || '''' || ',''' ||  <!--参保-->
               extractValue(COLUMN_VALUE, '/row/aaz159') || '''' || ',''' ||  <!--参保ID-->
               extractValue(COLUMN_VALUE, '/row/yab139') || '''' || ',''' ||  <!--所属分中心-->
               extractValue(COLUMN_VALUE, '/row/aaz099') || '''' || ',''' ||  <!--发放信息ID-->
               extractValue(COLUMN_VALUE, '/row/yac120') || '''' || ',''' ||  <!--人员类型-->
               extractValue(COLUMN_VALUE, '/row/yac121') || '''' || ',''' ||  <!--人员类型-->
               extractValue(COLUMN_VALUE, '/row/aaa027') || '''' || ',''' ||  <!--统筹区编码-->
               extractValue(COLUMN_VALUE, '/row/aae235') || '''' || ',''' ||  <!--待遇享受终止时间-->
               extractValue(COLUMN_VALUE, '/row/yac516') || '''' || ',''' ||  <!--档案出生日期-->
               extractValue(COLUMN_VALUE, '/row/aab071') || '''' || ',''' ||  <!--退休申报单位-->
               extractValue(COLUMN_VALUE, '/row/aac082') || '''' || ',''' ||  <!--离退休登记类型-->
               extractValue(COLUMN_VALUE, '/row/aae140') || '''' || ',''' ||  <!--险种类型-->
               extractValue(COLUMN_VALUE, '/row/aac012') || '''' || ',''' ||  <!--个人身份-->
               extractValue(COLUMN_VALUE, '/row/aac013') || '''' || ',''' ||  <!--用工形式-->
               extractValue(COLUMN_VALUE, '/row/aac014') || '''' || ',''' ||  <!--专业技术职务级别-->
               extractValue(COLUMN_VALUE, '/row/aac015') || '''' || ',''' ||  <!--国家职业资格等级（技能人员等级）-->
               extractValue(COLUMN_VALUE, '/row/aac020') || '''' || ',''' ||  <!--行政职务级别-->
               extractValue(COLUMN_VALUE, '/row/aac055') || '''' || ',''' ||  <!--参加革命工作日期-->
               extractValue(COLUMN_VALUE, '/row/aac057') || '''' || ',''' ||  <!--离退休证号-->
               extractValue(COLUMN_VALUE, '/row/aac064') || '''' || ',''' ||  <!--退役军人类别-->
               extractValue(COLUMN_VALUE, '/row/aac065') || '''' || ',''' ||  <!--退役军衔级别-->
               extractValue(COLUMN_VALUE, '/row/aac081') || '''' || ',''' ||  <!--建国前老工人标识-->
               extractValue(COLUMN_VALUE, '/row/aac085') || '''' || ',''' ||  <!--原工商业者标识-->
               extractValue(COLUMN_VALUE, '/row/aac093') || '''' || ',''' ||  <!--最高荣誉称号级别代码-->
               extractValue(COLUMN_VALUE, '/row/aae200') || '''' || ',''' ||  <!--视同缴费月数-->
               extractValue(COLUMN_VALUE, '/row/aae201') || '''' || ',''' ||  <!--实际缴费月数-->
               extractValue(COLUMN_VALUE, '/row/aae203') || '''' || ',''' ||  <!--军龄折算月数-->
               extractValue(COLUMN_VALUE, '/row/aae204') || '''' || ',''' ||  <!--特殊工种折算月数-->
               extractValue(COLUMN_VALUE, '/row/aae206') || '''' || ',''' ||  <!--账户建立年月-->
               extractValue(COLUMN_VALUE, '/row/aae211') || '''' outstring <!--待遇核定年月-->
          FROM (SELECT sys.xmlType.createXML(FUN_GetAc60_PEN(
                                                         a.aac001,
		                                                 a.aac002,
		                                                 a.aac003,
		                                                 a.aac004,
		                                                 a.aac005,
		                                                 a.aac006,
                                                         #aae140#,
                                                         #userid#,
                                                         #menuid#)) as ac60
                  FROM ac01 a
                 WHERE CATSEARCH(a.QUERYCOL,
                                 regexp_replace(#jstj#, '[ ]+', ' and '),
                                 NULL) > 0) p,
               TABLE(xmlsequence(extract(p.ac60, '/root/row'))) t
         <![CDATA[ WHERE ROWNUM<=20 ]]>
   </select>

   <!-- 退休后人员基本信息查询(弹出窗口)  -->
   <select id="getRetireInfoForWin" parameterClass="java.util.HashMap" resultClass="java.util.HashMap">
          SELECT A.AAC001, <!-- 个人编号 -->
                 A.AAC002, <!-- 身份证号 -->
                 A.AAC003, <!-- 姓名 -->
                 C.aic161, <!-- 离退休类别 -->
                 E.AAE044, <!-- 单位名称 -->
                 D.AAB019, <!-- 单位类型 -->
                 A.AAC004, <!-- 性别 -->
                 A.AAC005, <!-- 民族 -->
                 A.AAC006, <!-- 出生日期 -->
                 B.AAE116, <!-- 待遇发放状态 -->
                 C.aic162, <!-- 离退休时间 -->
                 B.AAB001, <!-- 单位ID -->
                 B.AAE210, <!-- 待遇享受开始年月 -->
                 B.YAC001, <!-- 个人最大发放期号 -->
                 B.AAZ257, <!-- 享受定期待遇人员ID -->
                 (SELECT NVL(MAX(AAZ157), 0) FROM AC20 WHERE AAZ159 = B.AAZ159) AS AAZ157, <!-- 人员社保保险关系ID -->
                 B.AAZ159, <!-- 人员参保关系ID -->
                 B.YAB139, <!-- 参保所属机构 -->
                 B.AAA027, <!-- 统筹区编号 -->
                 B.AAZ099  <!-- 发放途径ID -->
            FROM AC01 A, V_AC60 B, ic10 C, ab01 d, ae10 E
           WHERE A.AAC001 = B.AAC001
             AND B.AAZ257 = C.AAZ257
             AND B.AAb001 = D.AAb001
             AND D.AAb001 = E.AAZ001
             AND B.AAE140 = #aae140#
             AND B.USERID = #userid#
             AND B.MENUID = #menuid#
           <isNotEmpty prepend="AND" property="aac001"> 
                     A.AAC001 = #aac001#
             </isNotEmpty>    
           <isNotEmpty prepend="AND" property="aac002"> 
                     A.AAC002 = #aac002#
             </isNotEmpty>   
           <isNotEmpty prepend="AND" property="aac003"> 
                     A.AAC003 = #aac003#
             </isNotEmpty>
   </select>  
```
