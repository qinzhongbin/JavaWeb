# JSP
1. 概念：Java Server Pages java服务器端页面
   * 可以理解为：一个特殊的页面，其中既可以定义HTML标签，又可以定义java代码
   * 用于简化书写！！！
2. 原理：JSP本质上就是一个Servlet
3. JSP的脚本：JSP定义Java代码的方式
    1. <%  代码 %>：定义的java代码，在service方法中。service方法中可以定义什么，该脚本就可以定义什么。
    2. <%! 代码 %>：定义的java代码，在jsp转换后的java类成员位置。
    3. <%= 代码 %>：定义的java代码，会输出到页面上。输出语句中可以定义什么，该脚本据可以定义什么。
4. JSP内置的对象
    * 在jsp页面中不需要获取和创建，就可以直接使用的对象。
    * jsp一共有9个内置对象。
    
    | 变量名 | 真实类型 | 作用 |
    | --- | --- | --- |
    | pageContext   | PageContext        | 当前页面共享数据，还可以获取其他八个内置对象 |
    | request       | HttpServletRequest | 一次请求访问的多个资源（转发） |
    | session       | HttpSession        | 一次会话的多个请求间 |
    | application   | ServletContext     | 所有用户间共享数据 |
    | response      | HttpServletResponse| 响应对象 |
    | page          | Object             | 当前页面（Servlet）的对象 this |
    | out           | JspWriter          | 输出对象，数据输出到页面上 |
    | config        | ServletConfig      | Servlet的配置对象 |
    | exception     | Throwable          | 异常对象 |
   
    * out：字符输出流对象。可以将数据输出到页面上，和response.getWriter()类似。
        * response.getWriter()和out.writer()的区别：
            * 在tomcat服务器真正给客户端做出响应之前，会先找response缓冲区数据，再找out缓冲区数据。
            * response.getWriter()数据输出永远在out.writer()之前
5. 指令：
    * 作用：用于配置jsp页面，导入资源文件
    * 格式：<%@ 指令名称 属性名1=属性值1 属性名2=属性值2 ... %>
    * 分类：
        1. page: 配置JSP页面的
           * contentType: 等同于response.setContentType()
                1. 设置响应体的mime类型以及字符集
                2. 设置当前jsp页面的编码（只能是高级的IDE才能生效，如果使用低级工具，则需要设置pageEncoding属性设置当前页面的字符集）
            * import: 导包
            * errorPage: 当前页面发生异常后，会自动跳转到指点的错误页面
            * isErrorPage: 标识当前页面是否为错误页面
                * true: 可以使用内置对象exception
                * false: 默认值，不可使用exception内置对象
        2. include：导入页面资源文件
            * <%@include file="top.jsp" %>
        3. taglib: 导入资源
            * <%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
                * prefix：前缀，自定义的
6. 注释
    1. html注释：<!-- --> 只能注释html代码片段
    2. jsp注释：<%-- --> 可以注释所有
    