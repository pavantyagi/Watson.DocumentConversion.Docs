Personality Insights
==============

The Watson Personality Insights service_ uses linguistic analytics to extract a spectrum of cognitive and social characteristics from the text data that a person generates through blogs, tweets, forum posts, and more.

.. _service: https://www.nuget.org/packages/Watson.PersonalityInsights/
	
GetProfileAsync
----------------

Gets a PersonalityProfile based on the string content to analyze.

::

        public async Task GetProfile()
        {
            var service = new PersonalityInsightsService("USERNAME", "PASSWORD");
            var profile = await service.GetProfileAsync("SAMPLE_CONTENT");
        }
		
You may also use ProfileOptions to configure additional options.

::

        public async Task GetProfileWithOptions()
        {
            var options = new ProfileOptions("SAMPLE_CONTENT")
            {
                IncludeRaw = true,
                AcceptLanguage = AcceptLanguage.En
            };
            var service = new PersonalityInsightsService("USERNAME", "PASSWORD");
            var profile = await service.GetProfileAsync(options);
        }
		
You may also pass in multiple items using the Content class.

::

        public async Task GetProfileWithMultipleItems()
        {
            var content1 = "SAMPLE_CONTENT1";
            var content2 = "SAMPLE_CONTENT2";

            var contentItems = new List<ContentItem>
            {
                new ContentItem(content1),
                new ContentItem(content2)
            };

            var content = new Content(contentItems);
            var options = new ProfileOptions(content);
            var service = new PersonalityInsightsService("USERNAME", "PASSWORD");
            var profile = await service.GetProfileAsync(options);
        }
		
GetProfileAsCsvAsync
----------------

Gets a PersonalityProfile in Csv format based on multiple content items to analyze.

::

        public async Task GetProfileAsCsv()
        {
            var service = new PersonalityInsightsService("USERNAME", "PASSWORD");
            var profile = await service.GetProfileAsCsvAsync("SAMPLE_CONTENT");
        }
		
You may also use ProfileOptions to configure additional options.

::

        public async Task GetProfileAsCsvWithOptions()
        {
            var options = new ProfileOptions("SAMPLE_CONTENT")
            {
                IncludeRaw = true,
                IncludeCsvHeaders = true,
                AcceptLanguage = AcceptLanguage.En
            };
            var service = new PersonalityInsightsService("USERNAME", "PASSWORD");
            var profile = await service.GetProfileAsCsvAsync(options);
        }
		
You may also pass in multiple items using the Content class.

::

        public async Task GetProfileAsCsvWithMultipleItems()
        {
            var content1 = "SAMPLE_CONTENT1";
            var content2 = "SAMPLE_CONTENT2";

            var contentItems = new List<ContentItem>
            {
                new ContentItem(content1),
                new ContentItem(content2)
            };

            var content = new Content(contentItems);
            var options = new ProfileOptions(content);
            var service = new PersonalityInsightsService("USERNAME", "PASSWORD");
            var profile = await service.GetProfileAsCsvAsync(options);
        }