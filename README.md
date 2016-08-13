#Custom JMeter sampler for authenticated S3 requests

This is a custom java sampler class that can be used to benchmark any S3 compatible system.
It was tested against AWS and RIAK-CS 1.3.1.

Version 0.1 (alpha) 
 
Written by: Alex Bordei @ Bigstep
(alex at bigstep dt com)

##Dependencies:
* apache jmeter sources 2.11 
* AWS SDK 1.8.1

##How to use
Build using maven

	mvn package
	
Extract zip into JMeter directory

	cd jmeter_home
	unzip path/to/jmeter_s3_custom_sampler/target/*.zip 


Here is a typical list of the zip file contents :


   creating: lib/
   creating: lib/ext/
  inflating: lib/ext/jmeter-s3-sampler-0.1.jar  
  inflating: lib/httpclient-4.2.6.jar  
  inflating: lib/bcprov-jdk15on-1.49.jar  
  inflating: lib/xmlbeans-2.3.0.jar  
  inflating: lib/mongo-java-driver-2.11.3.jar  
  inflating: lib/joda-time-2.2.jar   
  inflating: lib/avalon-framework-4.1.4.jar  
  inflating: lib/bcmail-jdk15on-1.49.jar  
  inflating: lib/commons-io-2.4.jar  
  inflating: lib/excalibur-datasource-1.1.1.jar  
  inflating: lib/excalibur-pool-1.2.jar  
  inflating: lib/htmllexer-2.1.jar   
  inflating: lib/jcharts-0.7.5.jar   
  inflating: lib/vorbis-java-tika-0.1.jar  
  inflating: lib/vorbis-java-core-0.1-tests.jar  
  inflating: lib/netcdf-4.2-min.jar  
  inflating: lib/jackson-databind-2.1.1.jar  
  inflating: lib/commons-jexl-1.1.jar  
  inflating: lib/commons-lang3-3.1.jar  
  inflating: lib/soap-2.3.1.jar      
  inflating: lib/xz-1.2.jar          
  inflating: lib/pdfbox-1.8.1.jar    
  inflating: lib/jackson-annotations-2.1.1.jar  
  inflating: lib/httpcore-4.2.5.jar  
  inflating: lib/jorphan-2.11.jar    
  inflating: lib/commons-httpclient-3.1.jar  
  inflating: lib/commons-jexl-2.1.1.jar  
  inflating: lib/httpmime-4.2.6.jar  
  inflating: lib/oro-2.0.8.jar       
  inflating: lib/logkit-2.0.jar      
  inflating: lib/tika-core-1.4.jar   
  inflating: lib/fontbox-1.8.1.jar   
  inflating: lib/poi-scratchpad-3.9.jar  
  inflating: lib/geronimo-stax-api_1.0_spec-1.0.1.jar  
  inflating: lib/tagsoup-1.2.1.jar   
  inflating: lib/asm-debug-all-4.1.jar  
  inflating: lib/xmpcore-5.1.2.jar   
  inflating: lib/xercesImpl-2.9.1.jar  
  inflating: lib/activation-1.1.jar  
  inflating: lib/geronimo-jms_1.1_spec-1.1.1.jar  
  inflating: lib/jodd-core-3.4.10.jar  
  inflating: lib/jackson-core-2.1.1.jar  
  inflating: lib/ApacheJMeter_core-2.11.jar  
  inflating: lib/slf4j-api-1.7.5.jar  
  inflating: lib/apache-mime4j-core-0.7.2.jar  
  inflating: lib/apache-mime4j-dom-0.7.2.jar  
  inflating: lib/bcmail-jdk15-1.45.jar  
  inflating: lib/poi-ooxml-3.9.jar   
  inflating: lib/dom4j-1.6.1.jar     
  inflating: lib/isoparser-1.0-RC-1.jar  
  inflating: lib/jdom-1.0.jar        
  inflating: lib/xmlpull-1.1.3.1.jar  
  inflating: lib/xpp3_min-1.1.4c.jar  
  inflating: lib/xalan-2.7.1.jar     
  inflating: lib/aws-java-sdk-s3-1.9.0.jar  
  inflating: lib/bsf-2.4.0.jar       
  inflating: lib/bcpkix-jdk15on-1.49.jar  
  inflating: lib/excalibur-instrument-1.0.jar  
  inflating: lib/excalibur-logger-1.1.jar  
  inflating: lib/rhino-1.7R4.jar     
  inflating: lib/poi-ooxml-schemas-3.9.jar  
  inflating: lib/aws-java-sdk-core-1.9.0.jar  
  inflating: lib/commons-collections-3.2.1.jar  
  inflating: lib/htmlparser-2.1.jar  
  inflating: lib/hamcrest-core-1.3.jar  
  inflating: lib/jtidy-r938.jar      
  inflating: lib/commons-compress-1.5.jar  
  inflating: lib/jempbox-1.8.1.jar   
  inflating: lib/bcprov-jdk15-1.45.jar  
  inflating: lib/aspectjrt-1.6.11.jar  
  inflating: lib/metadata-extractor-2.6.2.jar  
  inflating: lib/boilerpipe-1.1.0.jar  
  inflating: lib/rome-0.9.jar        
  inflating: lib/xstream-1.4.4.jar   
  inflating: lib/xmlgraphics-commons-1.5.jar  
  inflating: lib/jodd-lagarto-3.4.10.jar  
  inflating: lib/slf4j-nop-1.7.5.jar  
  inflating: lib/ApacheJMeter_java-2.11.jar  
  inflating: lib/ApacheJMeter_components-2.11.jar  
  inflating: lib/commons-logging-1.1.3.jar  
  inflating: lib/commons-codec-1.8.jar  
  inflating: lib/bsh-2.0b5.jar       
  inflating: lib/junit-4.11.jar      
  inflating: lib/commons-net-3.3.jar  
  inflating: lib/jdom-1.1.3.jar      
  inflating: lib/tika-parsers-1.4.jar  
  inflating: lib/poi-3.9.jar         
  inflating: lib/xml-apis-1.3.04.jar  
  inflating: lib/vorbis-java-core-0.1.jar  
  inflating: lib/juniversalchardet-1.0.3.jar  
  inflating: lib/serializer-2.7.1.jar  
  inflating: lib/mail-1.5.0-b01.jar  
  inflating: lib/jsoup-1.7.3.jar     
  inflating: lib/rsyntaxtextarea-2.5.1.jar


Run jmeter as ususual
 
	sh ./bin/jmeter.sh 


Add a new jmeter Java sampler, use the com.bigstep.S3Sampler class.
![Alt text](/img/jmeter1.png?raw=true "Select jmeter custom sampler")

Add your AWS key id, bucket, object and the rest.
![Alt text](/img/jmeter2.png?raw=true "Configure jmeter sampler")

When testing against another system then AWS use the proxy settings to redirect requests somewhere else. Please note that the requests will still have the original host header pointing to amazonaws.com but the system should handle the requests nontheless.

Only GET and PUT methods are currently implemented but others should be very easy to add. 

