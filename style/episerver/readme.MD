QA list for Backend CMS 7.5+ MVC
Source code and database
* The project is easy to retrieve from source control.
* The project builds without warnings.
* The project only contains files that are in use.
* The project does not contain any empty folders.
* Files included in the project exist in source control.
* Commits are organised in appropriate chunks with descriptive comments.
* There's a separate branch for the production version.
* There are no remains from already merged feature branches/pull requests.
* The solution is properly set up on the build server.
* Assemblies get their version set properly when deploying from the build server.
* Deployments to test and production environments are controlled by the build/deplpoyment server. If it's not possible due to restrictions set by the hosting provider, this is described in the project readme.
* There exists a readme-file with a link to the correct wiki-page for the project + info that's required to run the solution locally on a developer machine.
* User and environment specific files (.user, .suo...) are not included in the source control.
* The database name is not prefixed with "db".

Config files and other settings
* The solution runs in IISExpress and IIS7+ with no hazzle.
* If a separate, custom IIS setup is required, this is automated through scripts described in the readme file.
* Configuration is split into logical files, with all necessary transformations for every relevant environment.
* appSettings.config does not contain things that might be interesting for an editor/admin to change.
* Blob storage points at a file share, and not a developer's local disk.
* Module settings in the project are sensible, and their editing controls make sense.
* Broadcast events for setting changes in load balanced environments are implemented.
* web.config/httpErrors is transformed to Custom or DetailedLocalOnly in production, but Detailed or DetailedLocalOnly in test/development environments.
* httpCacheVaryByParams contains all necessary query string parameter names.
* MIME types are properly configured for every file type in the file archive.
* AppData is set to a relative path in EPiServerFramework.config.
* Licenses are included in the solution for every environment (test, staging, production, development...)
* web.config/compilation debug="true" is transformed away when deploying with Release.Prod

Editor friendliness
* There are no unused page types.
* There are no unused blocks.
* Page type properties are sorted in a logical manner.
* Block properties are sorted in a logical manner.
* Page type properties are organized properly with tabs.
* Block properties are organized properly with tabs.
* Required and Searchable attributes are used for page types.
* Required and Searchable attributes are used for blocks.
* Page type properties have appropriate default values.
* Block properties have appropriate default values.
* Page type names and properties are translated and have suitable description texts.
* Block names and properties are translated and have suitable description texts.
* Visitor groups and gadgets are translated.
* Help texts, module text content etc. is translated.
* Max amount of versions of a page is limited.
* Available page types are restricted appropriately (not all page types should be available everywhere).
* On page editing works on basic content (texts, headings, content areas)
* The image editor is activated and has appropriate preset values.
* Content type properties with incrementing numbered names ("BodyText1", "BodyText2") is kept to an absolute minimum.
* Local blocks are used to group properties.
* Previewing content in different channels (iPhone, iPad...) is set up.
* Blocks and page types has images for preview/display (ImageUrlAttribute)
* Content types that should have but not necessarily have to have content should be validated (IValidate<T>). For example, a calendar event should propbably have a start and end date, but it might be valid with just the start date too.

Administrator friendliness
* There are no unused groups or virtual roles.
* Access rights for editors can easily be controlled from admin mode, and does not require changes to web.config.

Technical quality
* The solution can display simple EPiServer pages without crashing if integrations are unavailable/removed.
* The solution is appropriately split into projects.
* Logging is implemented and set up to log to a database.
* Content type models have suitable inheritance hierarchies.
* Mechanisms for proper archiving is implemented, to avoid pages with thousands of child pages on the same level.
* Controllers and view models have appropriate base classes to avoid duplicating code.
* Namespaces and naming in general is easy to understand, and allows reuse. ("CustomIntranetLeftMenu" vs "NestedMenuList" style naming)
* There is no home made URL generating. URLResolver is used where external addresses are required (i.e. feeds, data for external systems).
* Access modifiers are used correctly - not every method should be public.
* Controller actions have suitable annotations for things like ChildAction, Post etc.
* Dates, time, currencies, numeric values etc. are formatted based on CurrentUICulture, not hard coded formats.
* Third party components are updated.
* Content areas, XHTML string properties and Content reference properties are limited by AllowedTypes or equivalents where it's obvious that only certain types of content should be inserted.
* There is a global error page.
* Views does not contain stupid amounts of unnecessary line breaks or spacing.
* There are no unnecessary blocks for images/flash/other things that could be solved directly in TinyMCE.
* Extension methods are not overused.
* There are no remaining TODOs.
* There is no commented out code.
* For h1 elements, Heading is used - not PageName.
* All static files should return with HTTP status code 304.
* Bundling of CSS and JS files is implemented.
* All content type properties exists in code.
* If NuGets are updated, older versions of them are removed.
* The site runs as it should without being logged in (if it's a public site).
* Classes in the solution has a logically limited area of responsibility (Single responsibility principle).
* Dependency injections are used to tie the solution together. ServiceLocator is only used directly where one can't get things via the class constructor (like in scheduled jobs or event handlers).
* Dependencies to classes (except dumb POCOs) are retrieved in the constructors as interfaces, not concrete implementations.
* OPE doesn't ruin markup (extra DIVs etc).
* Controllers for partial views have an actual purpose.
* Exceptions aren't swallowed (caught but not handled). If they are, it is crystal clear from the context why.
* Client side code is not written as strings in the back end.
* No standalone modules/libraries are included in the solution as projects. This goes for the develop and master branches. Can be done for debugging in other branches.
* If your solution relies on DLL's, executables or the like existing on specific locations in the application, there are build events and deploy scripts to put them where needed. They are stored in separate folders for tools/libs outside the web root in the source code.
* If you're using ASP.NET WebAPI: method naming is used as they are intended to be: Get, Post, Put and Delete. Every controller has one responsibility - not both "GetUsers" and "GetDepartments" in one controller.
* If using EPiServer Find: If doing custom indexing of large amounts of data, these are split up during indexing instead of attempting to pass thousands of objects to Find in one request.
* Controller logic is limited to data retrieval and presentational logic. No typical business logic or "application service methods" exists in the controllers.
* No business logic in views. Example: No view uses the ServiceLocator.
* No methods over 80 lines.
* The solution does not have an excessive amount of unused using statements.
* Views do not have a large amount of using statement. They belong in pages in Views/web.config.
* If you're using ViewBag multiple places, use constants when refering to them - don't repeat the string key all over the place.
* Controllers and service classes in the solution does not require interfaces in ther constructor that is never used.
* Large, central service classes aren't implemented as "static helper classes".
* Static classes have very limited dependencies to other classes.
* Addresses to external web services, APIs etc are stored as configuration values, not as hard coded strings.
* Naming styles are consistent across classes, properties, fields, methods etc. (this.contentLoader vs _contentLoader)
* Model classes do not contain logic depending on other classes. They can contain logic inspecting and performing simple processing of it's own data.
* Central integrations, if any, are covered to a degree by unit tests.
* Information (code, comments, logic) is not duplicated around the solution. Also goes for "almost exactly the same"-things that could be generalized somehow.
* If the site is multi lingual, all forms posting to page controllers are posting to the correct language version of the page.

Language settings
* Amount of active site languages is restricted.
* System language is set (usually to norwegian).
* Language files exist only for active languages.
* No hard coded texts in views - everything should exist in language files.
* Pages have a canonical tag for fallback language, if any.
* lang attribute is set on the html element.

Search
* Search results are bookmarkable (=> controlled with query strings, not POST parameters).
* All searchable content types have a sensible view in the search results.
* An empty result should tell you about "0 hits", not just return an empty page.
* One should be able to exclude pages from search with the HideFromSearch property.
* Don't display a million hits. Use paging, "Show more" or similar.
* If some form of custom sorting/filtering is done, the hit rank is preserved.

Security
* Tools, admin plugins etc. are secured (for example with a location in web.config or by using the AuthorizeAttribute).
* E-mail addresses aren't given away in clear text on public pages.
* If user generated content is output inside Javascript strings, this is encoded.
* The site prevents Click Jacking
* Controller actions (both plain MVC controllers, page controllers and WebAPI-controllers) that are only reachable for certain users are locked down either by AuthorizeAttribute or (if possible) page access rights.
* File uploads checks file type (for example, .html or .exe files shouldn't be uploadable. Some sort of editor will end up opening it, and if it's full of bogus, things happen...)

Development environment
* Google Analytics (or equivalent) is not running in development and test environments.
* If the database is to be moved into production, there's a separate content structure for test content.
* Pornalizer and "funny pictures" are not used to add placeholder content. Generic "lorem ipsum" and non-offensive pictures are nice.
* Correct build actions are set for all files in the solution.
* SiteURL is set correctly in admin mode.
* episerverFramework.config contains all necessary removeAssemblies.
* All nugets exist in /packages on solution level, not beneath one specific project.
* Test, demo and stage environments
* If the solution is set up in our own demo environment, it's locked down from anonymous access.
* Robots.txt disallows everything.
* Cache folder for scaled images is moved out of the application directory.

Production environment
* Existing important links are handled when rolling out the new site to preserver page ranking in search engines.
* Languages are set up per host name in admin mode => config. This to avoid urls like www.epinova.no/en.
* The site replies to either mysite.com or www.mysite.com - not both. Redirect to the canonical variant is set up.
* Image files etc. from HTML mockups isn't part of the deployment.
* robots.txt exists with appropriate content.
* Test users are removed from the database.
* A complete system documentation exists on the wiki with all necessar information, and the info that's there is recently updated.
* Sending e-mail is configured and tested.
* Unnecessary HTTP headers are not passed to the client. Can be checked on Asafaweb.
* If SSL is used (commerce sites, restricted areas, sensitive data), the entire site auto redirects from HTTP to HTTPS.
* When using SSL, all resources included (Scripts, images...) should also be served over HTTPS.
* The wiki documentation does not duplicate config file content or other things that are present in the source code.
* Cache folder for scaled images is moved out of the application directory.
* In addition to this, we have free text areas for "Miscellaneous" and "Summary" to point out every other thing that we might find during the checking. 
