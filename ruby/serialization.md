# Serialization

Ruby I/O class has alises for `$stdin, $stdout, $stderr`

Serialization is basically "stringifying" an object's state. We can use Ruby's `I/O` class to send that serialzation anywhere: to a socket (web or otherwise) or to a file.

Three primary serialization methods in Ruby

- YAML
    - Human readable, can easily convert deeply nested object hierarchies, even on custom classes.
- JSON
    - Also human readable, can also easily convert deeply nested objects, but take to make sure the object is JSON-able.
- MessagePack
    - Binary format serialization. Fast, not human readable.

### File class

File has its own `puts` and `write` methods, analogous to `puts` and `print` in a terminal program. The latter in each pair does not end the output with a newline.

It is possible to pass `[File.open](http://File.open)` a block. This method has the advantage of closing the file automatically after the block completes, so if you only need to do one thing with a file, that's the way to go.

```ruby
somefile = File.open("sample.txt", "w")
somefile.puts "Hello file!"
somefile.close
```

One way to read a whole file is:

```ruby
file = File.open('sample.txt', 'r')
until file.eof?
	line = file.readline
end
```