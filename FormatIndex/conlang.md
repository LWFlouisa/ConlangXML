## Processing Marshall Locally
Marshalling data is processed on the local machine rather than on a web server, such as localhost.

### Marshalling XML In Ruby
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

### Extracting Data For Processing Into RSS Over IPFS
~~~ruby
# Reading in bin files, and processing into an RSS feed.
gender_bin      = File.read("_data/gender.bin")
noun_bin        = File.read("_data/noun.bin")
adjective_bin   = File.read("_data/adjective.bin")
conjucation_bin = File.read("_data/conjucation.bin")
verb_bin        = File.read("_data/verb.bin")
adverb_bin      = File.read("_data/adverb.bin")
punctuation_bin = File.read("_data/punctuation.bin")

# Deserialize the serialized data
gender      = Marshal.load(gender_bin)
noun        = Marshal.load(noun_bin)
adjective   = Marshal.load(adjective_bin)
conjucation = Marshal.load(conjucation_bin)
verb        = Marshal.load(verb_bin)
adverb      = Marshal.load(adverb_bin)
punctuation = Marshal.load(punctuation_bin)

puts "#{gender[1]} #{noun[1]} #{adjective[1]} #{conjucation[1]} #{verb[1]} #{adverb[1]}#{punctuation[1]}

"

puts "#{gender[0]}      #{gender[1]}"
puts "#{noun[0]}        #{noun[1]}"
puts "#{adjective[0]}   #{adjective[1]}"
puts "#{conjucation[0]} #{conjucation[1]}"
puts "#{verb[0]}        #{verb[1]}"
puts "#{adverb[0]}      #{adverb[1]}"
puts "#{punctuation[0]} #{punctuation[1]}"
~~~

# Preparing For Distribution Over IPFS
Process for deserialization and preparing as an RSS feed.

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
