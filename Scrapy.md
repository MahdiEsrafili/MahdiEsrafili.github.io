# How to use Scrapy!

first creating a virtual environment with conda.

after that, inspect the element you want with brower.

<pre><code>
scrapy shell http://example.com

response.css('element name::text').extract_first()

</code></pre>

or use spider!

create spider with:

<pre><code>
spider genspider <name> <site url>
</code></pre>

then edit the <name>.py and scrapy runspider <name>.py -o json