Document Conversion
==============

The Watson Document Conversion service_ converts a single HTML, PDF, or Microsoft Word document into a normalized HTML, plain text, or a set of JSON-formatted Answer units that can be used with other Watson services.

.. _service: https://www.nuget.org/packages/Watson.DocumentConversion/
	
ConvertDocumentToAnswersAsync
----------------

Converts a document to Answer Units.

::

        public async Task ConvertDocumentToAnswers()
        {
            var service = new DocumentConversionService("USERNAME", "PASSWORD");
            IAnswers answers;

            using (var fs = new FileStream("FILE_NAME", FileMode.Open))
            {
                answers = await service.ConvertDocumentToAnswersAsync(fs, FileType.FILE_TYPE);
            }
        }
		
ConvertDocumentToHtmlAsync
----------------

Converts a document to HTML.

::

        public async Task ConvertDocumentToHtml()
        {
            var service = new DocumentConversionService("USERNAME", "PASSWORD");
            string html;

            using (var fs = new FileStream("FILE_NAME", FileMode.Open))
            {
                html = await service.ConvertDocumentToHtmlAsync(fs, FileType.FILE_TYPE);
            }
        }
		
		