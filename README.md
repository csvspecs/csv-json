# CSV <3 JSON Format 

_CSV (Line-by-Line) Records with JSON Encoding Rules - A Modern (Simple) Tabular Data Format incl. Arrays, Numbers, Booleans, Nulls, Nested Structures, Comments and More_







## No CSV <3 JSON Parser in Your Language? Do-It-Yourself (DIY)

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


## Inspirtation / Heritage

### JSON Array Line by Line

- CSVJSON Format, see <> and
  - What's differnt?
    - No comments, comments, comments.
    - Uses a (simple ad-hoc) inline (optional) header schema format e.g. ``
    
### JSON Value(s) Line by Line

- JSON Lines
- Newline Delimited JSON (NDJSON)



## License

The CSV <3 JSON format is dedicated to the public domain.

