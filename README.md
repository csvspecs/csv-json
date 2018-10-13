# CSV <3 JSON Format 

_CSV (Line-by-Line) Records with JSON Encoding Rules - A Modern (Simple) Tabular Data Format incl. Arrays, Numbers, Booleans, Nulls, Nested Structures, Comments and More_



## CSV <3 JSON By Example


```
# "Vanilla" CSV <3 JSON

1,"John","12 Totem Rd. Aspen",true
2,"Bob",null,false
3,"Sue","Bigsby, 345 Carnival, WA 23009",false
```

or

```
# "Vanilla" CSV <3 JSON (Pretty Printed)

1, "John", "12 Totem Rd. Aspen",            true
2, "Bob",  null,                            false
3, "Sue", "Bigsby, 345 Carnival, WA 23009", false
```

or

```
# CSV <3 JSON with header / headers row

"id","name","address","regular"
1,"John","12 Totem Rd. Aspen",true
2,"Bob",null,false
3,"Sue","Bigsby, 345 Carnival, WA 23009",false
```

or

```
# CSV <3 JSON with values containing quotes and commas

"id","name","address","regular"
1,"John","12 Totem Rd., Aspen",true
2,"Bob",null,false
3,"Sue","\"Bigsby\", 345 Carnival, WA 23009",false
```

or

```
# CSV <3 JSON with array values

1,"directions",["north","south","east","west"]
2,"colors",["red","green","blue"]
3,"drinks",["soda","water","tea","coffe"]
4,"spells",[]
```	

or

```
# CSV with all kinds of values

"index","value1","value2"
"number",1,2
"boolean",false,true
"null",null,"non null"
"array of numbers",[1],[1,2]
"simple object",{"a": 1},{"a":1, "b":2}
"array with mixed objects",[1,null,"ball"],[2,{"a": 10, "b": 20},"cube"]
"string with quotes","a\"b","alert(\"Hi!\")"
"string with bell&newlines","bell is \u0007","multi\nline\ntext"
```



## Frequently Asked Questions (FAQ) and Answers

### Q: What's the recommended file type extension for CSV <3 JSON files?

The recommended file format for CSV <3 JSON files is `.csv` :-) or use `.json.csv` (to highlight 
the fact of the JSON encoding rules).





## Do-It-Yourself (DIY) - No CSV <3 JSON Parser in Your Language? - Build Your Own 


Build your own parser:

- Read the input (e.g. string or file) line-by-line
  - If the line is blank (only whitespace), skip the line.
  - If the line starts with a hash mark (`#`), skip the comment line.
  - Otherwise wrap the line in (`[]`) and pass along to the JSON parser :-).
  
  
Example in Ruby:

``` ruby
def parse( input )
   records = []
   input.each_line do |line|
        
      ##  note: chomp('') if is an empty string,
      ##    it will remove all trailing newlines (e.g. \n or \r\n) from the line
      line = line.chomp( '' )
      
      ##  strip leading and trailing whitespaces (space and tab)
      line = line.strip
      
      next if line.empty?             ## skip blank lines
      next if line.start_with?( '#' ) ## skip comment lines
        
      ## note: auto-wrap in array e.g. with []
      records << JSON.parse( "[#{line}]" )
    end
    records
end
```



## Inspirtation / Heritage / Alternatives

### JSON Array Line by Line

- CSVJSON Format, see <http://csvjson.org>
  - What's differnt?
    - No comments, comments, comments.
    - Uses a (simple ad-hoc) inline (optional) header schema format e.g. `{"field":"id","type":"int"},{"field":"name","type":"string"}, ...`
    
    
### JSON Value(s) Line by Line

- JSON Lines, see <http://jsonlines.org>
- Newline Delimited JSON (NDJSON), see <http://ndjson.org>



## License

The CSV <3 JSON format is dedicated to the public domain.
