Advanced Options
==============

It is possible to configure the output of a document conversion by using the advanced_ options of the Document Conversion service. 
This is achieved by creating a JObject_ and passing it into the conversion method.

.. _JObject: http://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_Linq_JObject.htm
.. _advanced: http://www.ibm.com/smarterplanet/us/en/ibmwatson/developercloud/doc/document-conversion/customizing.shtml
	
Advanced customization can be tricky and it is advised to read the official docs first.

http://www.ibm.com/smarterplanet/us/en/ibmwatson/developercloud/doc/document-conversion/customizing.shtml

For example, let's assume that we want to exclude content in any <script> tags that may be in a Html page.
A JObject should be declared with the appropriate Json.

::

        var config = JObject.Parse("{\"normalize_html\":{\"exclude_tags_completely\":[\"script\"]}}");
		
The JObject can then be used in any standard method call.	
	
::
	
        public async Task ConvertDocumentToText()
        {
            var service = new DocumentConversionService("USERNAME", "PASSWORD");
            var config = JObject.Parse("{\"normalize_html\":{\"exclude_tags_completely\":[\"script\"]}}");
			
            string text;

            using (var fs = new FileStream("FILE_NAME", FileMode.Open))
            {
                text = await service.ConvertDocumentToTextAsync(fs, FileType.FILE_TYPE, config);
            }
        }
		

