# mybatis-gradle-plugin
Use DSL to config the mybatis generator

 
## DSL Usage
```groovy
mybatis{
    context {
        id "MySql"
        targetRuntime "Mybatis3"
        jdbcConnection{
            driverClass "com.mysql.jdbc.Driver"
            connectionURL "jdbc:mysql://localhost:3306/mmall?useUnicode=true&amp;characterEncoding=utf-8"
            userId "root"
            password "123456"
        }

        plugin "mybatis.DataSourcePlugin"

        commentGenerator{
            property "suppressAllComments", "true"
        }

        javaModelGenerator{
            targetProject "$project.projectDir/src/main/java"
            targetPackage "cn.yjwfn.model"
        }

        javaClientGenerator{
            targetProject "$project.projectDir/src/main/java"
            targetPackage "cn.yjwfn.dao"
            type "XMLMAPPER"
        }

        sqlMapGenerator{
            targetProject "$project.projectDir/src/main/resources"
            targetPackage "mapper"
        }

        tables{
            "mmall_user" {
                domainObjectName "User"
                generateKey "id","mysql",true
            }

            "mmall_product" {
                domainObjectName "Product"
                generateKey "id","mysql",true
            }
        }
    }
}
```