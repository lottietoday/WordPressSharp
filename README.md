#WordPressSharp#
A C# client to interact with the WordPress XML-RPC API

#Install#
I'm working on a Nuget package once I'm done mapping all the WP XML-RPC endpoints.

In the meantime, you'll have to clone, build, and add the DLL the ole fashioned way

#Config#
Use your config file to for configuration settings:
```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
	<appSettings>
		<add key="WordPressUsername" value="" />
		<add key="WordPressPassword" value="" />
		<add key="WordPressBaseUrl" value="" />
		<add key="WordPressBlogId" value="" />
	</appSettings>
</configuration>
```
As an alternative you can use the `WordPressSiteConfig` class to store configuration settings.


#Examples#
**Create Post**  

    var post = new Post {
        PostType = "post",
        Title = "My Awesome Post",
        Content = "<p>This is the content</p>",
        PublishDateTime = DateTime.Now
    };

    using (var client = new WordPressClient()) 
    {
        var id = Convert.ToInt32(client.NewPost(post));
    }

##Create Post Tag##

    using (var client = new WordPressClient())
    {
        var termId = client.NewTerm(new Term
        {
            Name = "term test",
            Description = "term description",
            Slug = "term_test",
            Taxonomy = "post_tag"
        });
    }

#Tutorials#
[How to publish a post or page](http://brudtkuhl.com/using-wordpresssharp-publish-post/)

#Dependencies#
[XML-RPC.net](http://xml-rpc.net/)

#Resources#
[WordPress XML-RPC API](http://codex.wordpress.org/XML-RPC_WordPress_API)

#Notes#
Inspired by the [POSSIBLE.WordPress.XmlRpcClient](https://github.com/markeverard/POSSIBLE.WordPress.XmlRpcClient) by [markeverard](https://github.com/markeverard)
