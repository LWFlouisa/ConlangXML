## A Possible XML Format
~~~xml
<rss>
<channel>
  <title>Natural Language Machine Diary</title>
  <link></link>
  <description>Local Feed for the Ahusacos Conlang.</description>    
  
  <item>
    <title></title>
    <link></link>
    <description>
      <example_sentence>
      <grammar context="phrase"><gender>#{gender}</gender><noun>#{noun}</noun><conjucation>#{conjucation}</conjucation><verb>#{verb}<verb><adverb>#{adverb}</adverb><punctuation>#{punctuation}</punctuation></grammar>
      <example_sentence>
        
      <collumn>
        <grammar context="phrase">
          <gender>#{gender}</gender>
          <noun>#{noun}</noun>
          <conjucation>#{conjucation}</conjucation>
          <verb>#{verb}<verb>
          <adverb>#{adverb}</adverb>
          <punctuation>#{punctuation}</punctuation>
        </grammar>
      </collumn>
          
    </description>
  </item>
</channel>
</rss>
~~~

## Marshalling XML In Ruby
How to generate a natural language xml from a marshall.

~~~ruby
~~~
