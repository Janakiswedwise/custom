Building extensions container image
-------------------------------------
-------------------------------------
OTMM :

	The root directory for placing all the custom extensions related to OTMM is "deploy-customizations/OTMM"
	 
1. Place all the customization libraries in "plugins" folder. Examples for customization libraries include : custom job step, custom transformers, custom content managers,custom java lookup domains, Asset Interceptors etc..
2. Place all the custom event listeners in "listeners" folder. All the custom event listeners should be registered in web.xml file.
	Example : You need to create a web.xml file with below content and place it in "conf" folder.
		
		<listener>
			   <listener-class>com.otmm.CustomEventListenerClass</listener-class>
		</listener>

3. Place all the ux customizations in "ux" folder.
4. Place all the J2EE archives(EARs) in "apps" folder. All the configurations pertaining to custom ear should be registered in tomee.xml file.
	Example : You need to create a tomee.xml file with below content and place it in "conf" folder
		
		<Deployments file="apps/Custom.ear"/>	

5. Place all the wars in "webapps" folder.
6. Place web.xml, tomee.xml configuration files in conf location. 

-----------------------------------------------------------------------------------------------------------

IntegrationService : 
	
	The root directory for placing all the custom extensions related to IntegrationService is "deploy-customizations/IS"

1. Place all the customization libraries in "plugins" folder.

------------------------------------------------------------------------------------------------------------

RMA : 

	The root directory for placing all the custom extensions related to RMA is "deploy-customizations/RMA"

1. Place all the customizations libraries in "plugins" folder.

------------------------------------------------------------------------------------------------------------

AMD :

	The root directory for placing all the custom extensions related to AMD is "deploy-customizations/AMD"

1. Place all the customization libraries in "lib" folder.
    Example : Create custom CDN class as per OpenText Media Management: Integration Guide with below steps
            a) Implement the com.opentext.adaptivemedia.interfaces.CDNCacheService interface.
            b) Extend the com.opentext.adaptivemedia.common.Tenant.BaseTenantService class.
            c) Then create a JAR file for the custom CDN class and then copy the JAR file to deploy-customizations/AMD/lib
2. In the otmm-extension-toolkit/deploy-customizations/AMD/conf folder, open the conf.properties file and set the value of CDNCacheService to com.opentext.adaptivemedia.service.impl.<CustomCDNImplFileName>.
   Example: CDNCacheService=com.opentext.adaptivemedia.services.impl.CustomCDNCacheServiceImpl

------------------------------------------------------------------------------------------------------------

Once all the customizations are copied, then build the extension container image using below command.

	docker build --file Dockerfile --tag <init-image-tag> .