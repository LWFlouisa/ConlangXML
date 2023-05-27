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
# Grammar Symbols, Specific Tokens, and its descriptors as strings.
gender      = :gender,      "Le",    "Gender"
noun        = :noun,        "pomme", "Noun"
adjective   = :adjective,   "rouge", "Adjective"
conjucation = :conjucation, "es",    "Conjucation"
verb        = :verb,        "tres",  "Verb"
adverb      = :adverb,      "grand", "Adverb"
punctuation = :punctuation, ".",     "Punctuation"

# Dumping individual grammatical components.
gender_dump      = Marshal.dump(gender)
noun_dump        = Marshal.dump(noun)
adjective_dump   = Marshal.dump(adjective)
conjucation_dump = Marshal.dump(conjucation)
verb_dump        = Marshal.dump(verb)
adverb_dump      = Marshal.dump(adverb)
punctuation_dump = Marshal.dump(punctuation)

# Write the serialized data to a file
File.write("gender.bin",           gender)
File.write("noun.bin",               noun)
File.write("adjective.bin",     adjective)
File.write("conjucation.bin", conjucation)
File.write("verb.bin",               verb)
File.write("adverb.bin",           adverb)
File.write("punctuation.bin", punctuation)
~~~
