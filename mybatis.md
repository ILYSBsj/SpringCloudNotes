### mybatis面试题
1、#{}.${}的区别：
    ~~前者有预处理后者是直接替换。前者preparestatement的set方法将值set进去，可以防止sql注入~~

    < #{}是预编译处理，${}是字符串替换。Mybatis 在处理#{}时，会将 sql 中的#{}替换为?号，调PreparedStatement 的set方法来赋值； 
    <Mybatis 在处理${}时，就是把${}替换成变量的值。使用#{}可以有效的防止 SQL 注入，提高系统安全性。

2、dao接口的原理，是否能重载：
    ~~dao接口是基于jdk实现的，jdk在请求接口后将找到这个dao方法匹配的xml方法（依靠id和名字），然后执行sql再将结果直接返回。~~

    < Dao 接口，就是人们常说的 Mapper 接口，接口的全限名，就是映射文件中的 namespace
    <的值，接口的方法名，就是映射文件中 MappedStatement 的 id 值，接口方法内的参数，
    <就是传递给 sql 的参数。Mapper 接口是没有实现类的，当调用接口方法时，接口全限名+
    <方法名拼接字符串作为 key 值，可唯一定位一个 MappedStatement，举例：
    <com.mybatis3.mappers.StudentDao.findStudentById，可以唯一找到 namespace 为
    <com.mybatis3.mappers.StudentDao 下面 id = findStudentById 的
    <MappedStatement。在 Mybatis 中，每一个<select>、<insert>、<update>、<delete>
    <标签，都会被解析为一个 MappedStatement 对象。
    <Dao 接口里的方法，是不能重载的，因为是全限名+方法名的保存和寻找策略。
    <Dao 接口的工作原理是 JDK 动态代理，Mybatis 运行时会使用 JDK 动态代理为 Dao
    <接 口 生 成 代 理 proxy 对 象 ， 代 理 对 象 proxy 会 拦 截 接 口 方 法 ， 转 而 执 行
    <MappedStatement 所代表的 sql，然后将 sql 执行结果返回。

3、mybatis的分页是如何实现的，分页原理是什么？
    ~~是通过rowband实现的，分页有物理分页和分页，插件分页是通过在sql后面拼接分页语句实现的~~
