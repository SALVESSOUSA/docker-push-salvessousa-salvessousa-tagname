# docker-push-salvessousa-salvessousa-tagname
Conveniecia
 projeto  default = " -deploy-ant "  basedir = " . " >
    < target  name = " -init "  if = " deploy.ant.enabled " >
        < property  file = " $ {deploy.ant.properties.file} " />
        < tabfile  property = " tab.module.folder "  prefix = " tomcat "  destdir = " $ {java.io.tmpdir} " />
        < unwar  src = " $ {deploy.ant.archive} "  dest = " $ {temp.module.folder} " 
        
            < patternset  includes = " META-INF / context.xml " />
        </ unwar >
        < xmlproperty  file = " $ {tab.module.folder} /META-INF/context.xml " />
        < delete  dir = " $ {temp.module.folder} " />
    </ target >
    < Meta  nome = " -check-credenciais "  se = " deploy.ant.enabled "  depende = " -init " >
        < fail  message = "A senha do Tomcat deve ser passada como propriedade tomcat.password. " >
            < condição >
                < não >
                    < isset  property = " tomcat.password " />
                </ não >
            </ condição >
        </ falha >
    </ target >
    < Meta  nome = " -Implante-tabela "  se = " deploy.ant.enabled "  depende = " -init, -check-credenciais " >
        < echo  message = " Implantando $ {deploy.ant.archive} em $ {Context (path)} " />
        < taskdef  name = " implantar "  classname = " org.apache.catalina.ant.DeployTask "
                 classpath = " $ {tomcat.home} /server/lib/catalina-ant.jar " />
        < deploy  url = " $ {tomcat.url} / manager "  username = " $ {tomcat.username} "
                senha = " $ {tomcat.password} "  path = " $ {Context (path)} "
                war = " $ {deploy.ant.archive} " />
        < property  name = " deploy.ant.client.url "  value = " $ {tomcat.url} $ {Context (path)} " />
    </ target >
    < Meta  nome = " -undeploy-formiga "  se = " deploy.ant.enabled "  depende = " -init, -check-credenciais " >
        < echo  message = " Desimplantando $ {Context (path)} " />
        < taskdef  name = " undeploy "   classname = " org.apache.catalina.ant.UndeployTask "
                classpath = " $ {tomcat.home} /server/lib/catalina-ant.jar " />
        < undeploy  url = " $ {tomcat.url} / manager "  username = " $ {tomcat.username} " 
                  senha = " $ {tomcat.password} "  path = " $ {Context (path)} " />
    </ target >
</ projeto >
