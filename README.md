# Yard-Junk: get rid of junk in your YARD docs!

[![Gem Version](https://badge.fury.io/rb/yard-junk.svg)](http://badge.fury.io/rb/yard-junk)
[![Build Status](https://travis-ci.org/zverok/yard-junk.svg?branch=master)](https://travis-ci.org/zverok/yard-junk)

Yard-Junk is [yard](https://github.com/lsegal/yard) plugin/patch, that provides:

* structured documentation error logging;
* documentation errors validator, ready to be integrated into CI pipeline.

## Showcase

Let's generate the docs for the [rom](https://github.com/rom-rb/rom) library.

<details><summary>Output of `yard doc` without JunkYard</summary>

```
[warn]: in YARD::Handlers::Ruby::MixinHandler: Undocumentable mixin: YARD::Parser::UndocumentableError for class ROM::Types
	in file 'core/lib/rom/types.rb':9:

	9: include Dry::Types.module

[warn]: Invalid tag format for @example in file `core/lib/rom/global.rb` near line 41
[warn]: in YARD::Handlers::Ruby::MixinHandler: Undocumentable mixin: YARD::Parser::UndocumentableError for class ROM::Schema
	in file 'core/lib/rom/schema.rb':66:

	66: include Dry::Equalizer(:name, :attributes, :associations)

[warn]: @param tag has unknown parameter name:
    in file `core/lib/rom/schema.rb' near line 149
[warn]: @param tag has unknown parameter name:
    in file `core/lib/rom/schema.rb' near line 305
[warn]: @param tag has unknown parameter name:
    in file `core/lib/rom/schema.rb' near line 316
[warn]: in YARD::Handlers::Ruby::MixinHandler: Undocumentable mixin: YARD::Parser::UndocumentableError for class ROM::Command
	in file 'core/lib/rom/command.rb':30:

	30: include Dry::Equalizer(:relation, :options)

[warn]: @param tag has unknown parameter name: Transaction
    in file `core/lib/rom/gateway.rb' near line 176
[warn]: in YARD::Handlers::Ruby::MixinHandler: Undocumentable mixin: YARD::Parser::UndocumentableError for class ROM::Pipeline::Composite
	in file 'core/lib/rom/pipeline.rb':82:

	82: include Dry::Equalizer(:left, :right)

[warn]: in YARD::Handlers::Ruby::MixinHandler: Undocumentable mixin: YARD::Parser::UndocumentableError for class ROM::Registry
	in file 'core/lib/rom/registry.rb':13:

	13: include Dry::Equalizer(:elements)

[warn]: in YARD::Handlers::Ruby::MixinHandler: Undocumentable mixin: YARD::Parser::UndocumentableError for class ROM::Relation
	in file 'core/lib/rom/relation.rb':129:

	129: include Dry::Equalizer(:name, :dataset)

[warn]: @param tag has unknown parameter name: options
    in file `core/lib/rom/relation.rb' near line 302
[warn]: @param tag has unknown parameter name: new_options
    in file `core/lib/rom/relation.rb' near line 411
[warn]: @param tag has unknown parameter name: klass
    in file `core/lib/rom/relation.rb' near line 529
[warn]: in YARD::Handlers::Ruby::MixinHandler: Undocumentable mixin: YARD::Parser::UndocumentableError for class ROM::Attribute
	in file 'core/lib/rom/attribute.rb':17:

	17: include Dry::Equalizer(:type, :options)

[warn]: @param tag has unknown parameter name:
    in file `core/lib/rom/attribute.rb' near line 344
[warn]: in YARD::Handlers::Ruby::MixinHandler: Undocumentable mixin: YARD::Parser::UndocumentableError for class ROM::Container
	in file 'core/lib/rom/container.rb':101:

	101: include Dry::Equalizer(:gateways, :relations, :mappers, :commands)

[warn]: @param tag has unknown parameter name: base
    in file `core/lib/rom/plugin_base.rb' near line 41
[warn]: in YARD::Handlers::Ruby::MixinHandler: Undocumentable mixin: YARD::Parser::UndocumentableError for class ROM::Commands::Lazy
	in file 'core/lib/rom/commands/lazy.rb':10:

	10: include Dry::Equalizer(:command, :evaluator)

[warn]: @param tag has unknown parameter name: The
    in file `core/lib/rom/configuration.rb' near line 50
[warn]: @param tag has unknown parameter name: Plugin
    in file `core/lib/rom/configuration.rb' near line 50
[warn]: in YARD::Handlers::Ruby::MixinHandler: Undocumentable mixin: YARD::Parser::UndocumentableError for class ROM::Relation::Name
	in file 'core/lib/rom/relation/name.rb':17:

	17: include Dry::Equalizer(:relation, :dataset)

[warn]: in YARD::Handlers::Ruby::MixinHandler: Undocumentable mixin: YARD::Parser::UndocumentableError for class ROM::Commands::Graph
	in file 'core/lib/rom/commands/graph.rb':12:

	12: include Dry::Equalizer(:root, :nodes)

[warn]: @param tag has unknown parameter name: names
    in file `core/lib/rom/memory/dataset.rb' near line 61
[warn]: in YARD::Handlers::Ruby::MixinHandler: Undocumentable mixin: YARD::Parser::UndocumentableError for class ROM::Relation::Graph
	in file 'core/lib/rom/relation/graph.rb':29:

	29: include Dry::Equalizer(:root, :nodes)

[warn]: in YARD::Handlers::Ruby::MixinHandler: Undocumentable mixin: YARD::Parser::UndocumentableError for class ROM::PluginRegistryBase
	in file 'core/lib/rom/plugin_registry.rb':88:

	88: include Dry::Equalizer(:elements, :plugin_type)

[warn]: Unknown tag @raises in file `core/lib/rom/plugin_registry.rb` near line 143
[warn]: Unknown tag @raises in file `core/lib/rom/plugin_registry.rb` near line 190
[warn]: in YARD::Handlers::Ruby::MixinHandler: Undocumentable mixin: YARD::Parser::UndocumentableError for class ROM::Relation::Loaded
	in file 'core/lib/rom/relation/loaded.rb':12:

	12: include Dry::Equalizer(:source, :collection)

[warn]: Unknown tag @raises in file `core/lib/rom/relation/loaded.rb` near line 94
[warn]: in YARD::Handlers::Ruby::MixinHandler: Undocumentable mixin: YARD::Parser::UndocumentableError for class ROM::Schema::Inferrer
	in file 'core/lib/rom/schema/inferrer.rb':27:

	27: include Dry::Equalizer(:options)

[warn]: @param tag has unknown parameter name: name
    in file `core/lib/rom/command_registry.rb' near line 57
[warn]: in YARD::Handlers::Ruby::MixinHandler: Undocumentable mixin: YARD::Parser::UndocumentableError for class ROM::Relation::Curried
	in file 'core/lib/rom/relation/curried.rb':22:

	22: include Dry::Equalizer(:relation, :options)

[warn]: Unknown tag @raises in file `core/lib/rom/relation/curried.rb` near line 72
[warn]: @param tag has unknown parameter name: adapter
    in file `core/lib/rom/global/plugin_dsl.rb' near line 42
[warn]: @param tag has unknown parameter name:
    in file `core/lib/rom/relation/combined.rb' near line 33
[warn]: in YARD::Handlers::Ruby::MixinHandler: Undocumentable mixin: YARD::Parser::UndocumentableError for class ROM::Associations::Abstract
	in file 'core/lib/rom/associations/abstract.rb':17:

	17: include Dry::Equalizer(:definition, :source, :target)

[warn]: in YARD::Handlers::Ruby::MixinHandler: Undocumentable mixin: YARD::Parser::UndocumentableError for class ROM::Notifications::Event
	in file 'core/lib/rom/support/notifications.rb':75:

	75: include Dry::Equalizer(:id, :payload)

[warn]: @param tag has unknown parameter name: command
    in file `core/lib/rom/commands/class_interface.rb' near line 86
[warn]: @param tag has unknown parameter name: parent
    in file `core/lib/rom/commands/class_interface.rb' near line 86
[warn]: @param tag has unknown parameter name: options
    in file `core/lib/rom/commands/class_interface.rb' near line 112
[warn]: @param tag has unknown parameter name:
    in file `core/lib/rom/commands/class_interface.rb' near line 123
[warn]: in YARD::Handlers::Ruby::MixinHandler: Undocumentable mixin: YARD::Parser::UndocumentableError for class ROM::Commands::Graph::InputEvaluator
	in file 'core/lib/rom/commands/graph/input_evaluator.rb':5:

	5: include Dry::Equalizer(:tuple_path, :excluded_keys)

[warn]: in YARD::Handlers::Ruby::MixinHandler: Undocumentable mixin: YARD::Parser::UndocumentableError for class ROM::Associations::Definitions::Abstract
	in file 'core/lib/rom/associations/definitions/abstract.rb':16:

	16: include Dry::Equalizer(:source, :target, :result)

[warn]: @param tag has unknown parameter name: options
    in file `core/lib/rom/associations/definitions/abstract.rb' near line 74
[warn]: @param tag has unknown parameter name: options
    in file `changeset/lib/rom/changeset.rb' near line 84
[warn]: in YARD::Handlers::Ruby::ClassHandler: Undocumentable superclass (class was added without superclass)
	in file 'changeset/lib/rom/changeset/pipe.rb':28:

	28: class Pipe < Transproc::Transformer[PipeRegistry]

[warn]: @param tag has unknown parameter name: assoc
    in file `changeset/lib/rom/changeset/stateful.rb' near line 222
[warn]: in YARD::Handlers::Ruby::MixinHandler: Undocumentable mixin: YARD::Parser::UndocumentableError for class ROM::Header
	in file 'mapper/lib/rom/header.rb':12:

	12: include Dry::Equalizer(:attributes, :model)

[warn]: @param tag has unknown parameter name: model
    in file `mapper/lib/rom/header.rb' near line 52
[warn]: in YARD::Handlers::Ruby::MixinHandler: Undocumentable mixin: YARD::Parser::UndocumentableError for class ROM::Mapper
	in file 'mapper/lib/rom/mapper.rb':11:

	11: include Dry::Equalizer(:transformers, :header)

[warn]: in YARD::Handlers::Ruby::MixinHandler: Undocumentable mixin: YARD::Parser::UndocumentableError for class ROM::Header::Attribute
	in file 'mapper/lib/rom/header/attribute.rb':14:

	14: include Dry::Equalizer(:name, :key, :type)

[warn]: in YARD::Handlers::Ruby::MixinHandler: Undocumentable mixin: YARD::Parser::UndocumentableError for class ROM::Header::Embedded
	in file 'mapper/lib/rom/header/attribute.rb':110:

	110: include Dry::Equalizer(:name, :key, :type, :header)

[warn]: @param tag has unknown parameter name:
    in file `mapper/lib/rom/processor/transproc.rb' near line 215
[warn]: in YARD::Handlers::Ruby::MixinHandler: Undocumentable mixin: YARD::Parser::UndocumentableError for class ROM::Session
	in file 'repository/lib/rom/repository/session.rb':8:

	8: include Dry::Equalizer(:queue, :status)

[warn]: The proxy Coercible has not yet been recognized.
If this class/method is part of your source tree, this will affect your documentation results.
You can correct this issue by loading the source file for this object before `core/lib/rom/types.rb'

[warn]: The proxy Coercible has not yet been recognized.
If this class/method is part of your source tree, this will affect your documentation results.
You can correct this issue by loading the source file for this object before `core/lib/rom/types.rb'

[warn]: The proxy Coercible has not yet been recognized.
If this class/method is part of your source tree, this will affect your documentation results.
You can correct this issue by loading the source file for this object before `core/lib/rom/types.rb'
```
</details>

Things to notice:

* irregular and frequently approximate addresses (`in file 'core/lib/rom/types.rb':9`,
  `in file 'core/lib/rom/global.rb' near line 41`, sometimes in separate line, sometimes inline),
  hard to jump-to with any tool;
* a lot of ununderstood metaprogramming (grep for "Undocumentable mixin") -- nothing to fix here,
  but YARD still notifies you;
* verbose and not very informative errors (look at that "Undocumentable mixin" -- and then grep
  for "The proxy Coercible has not yet been recognized." and compare).

<details><summary>Output of `yard doc` with Yard-Junk</summary>

```
core/lib/rom/global.rb:40: [InvalidTagFormat] Invalid tag format for @example
core/lib/rom/schema.rb:144: [MissingParamName] @param tag has empty parameter name
core/lib/rom/schema.rb:300: [MissingParamName] @param tag has empty parameter name
core/lib/rom/schema.rb:311: [MissingParamName] @param tag has empty parameter name
core/lib/rom/gateway.rb:171: [UnknownParam] @param tag has unknown parameter name: Transaction
core/lib/rom/relation.rb:297: [UnknownParam] @param tag has unknown parameter name: options
core/lib/rom/relation.rb:406: [UnknownParam] @param tag has unknown parameter name: new_options
core/lib/rom/relation.rb:524: [UnknownParam] @param tag has unknown parameter name: klass
core/lib/rom/attribute.rb:339: [MissingParamName] @param tag has empty parameter name
core/lib/rom/plugin_base.rb:38: [UnknownParam] @param tag has unknown parameter name: base. Did you mean `_base`?
core/lib/rom/configuration.rb:46: [UnknownParam] @param tag has unknown parameter name: The
core/lib/rom/configuration.rb:47: [UnknownParam] @param tag has unknown parameter name: Plugin. Did you mean `plugin`?
core/lib/rom/memory/dataset.rb:54: [UnknownParam] @param tag has unknown parameter name: names
core/lib/rom/plugin_registry.rb:140: [UnknownTag] Unknown tag @raises. Did you mean @raise?
core/lib/rom/plugin_registry.rb:187: [UnknownTag] Unknown tag @raises. Did you mean @raise?
core/lib/rom/relation/loaded.rb:91: [UnknownTag] Unknown tag @raises. Did you mean @raise?
core/lib/rom/command_registry.rb:52: [UnknownParam] @param tag has unknown parameter name: name
core/lib/rom/relation/curried.rb:69: [UnknownTag] Unknown tag @raises. Did you mean @raise?
core/lib/rom/global/plugin_dsl.rb:41: [UnknownParam] @param tag has unknown parameter name: adapter
core/lib/rom/relation/combined.rb:28: [MissingParamName] @param tag has empty parameter name
core/lib/rom/commands/class_interface.rb:78: [UnknownParam] @param tag has unknown parameter name: command
core/lib/rom/commands/class_interface.rb:79: [UnknownParam] @param tag has unknown parameter name: parent
core/lib/rom/commands/class_interface.rb:108: [UnknownParam] @param tag has unknown parameter name: options. Did you mean `_options`?
core/lib/rom/commands/class_interface.rb:118: [MissingParamName] @param tag has empty parameter name
core/lib/rom/associations/definitions/abstract.rb:66: [UnknownParam] @param tag has unknown parameter name: options
changeset/lib/rom/changeset.rb:79: [UnknownParam] @param tag has unknown parameter name: options. Did you mean `new_options`?
changeset/lib/rom/changeset/stateful.rb:219: [UnknownParam] @param tag has unknown parameter name: assoc
mapper/lib/rom/header.rb:47: [UnknownParam] @param tag has unknown parameter name: model
mapper/lib/rom/processor/transproc.rb:212: [MissingParamName] @param tag has empty parameter name
core/lib/rom/types.rb:1: [UnknownNamespace] namespace Coercible is not recognized
core/lib/rom/types.rb:1: [UnknownNamespace] namespace Coercible is not recognized
core/lib/rom/types.rb:1: [UnknownNamespace] namespace Coercible is not recognized
```
</details>

Things to notice:

* Regular output style with clearly recognizable addresses (and fixed to point at actual line with
  the problematic tag, not the method which tag is related for);
* Error classes, allowing grouping, grepping, and configuring (notice no "Undocumentable xxx" errors:
  I've just configured `yard-junk` to drop them for this repo);
* Usage of Ruby's bundled `did_you_mean` gem to show reasonable suggestions:
```
Unknown tag @raises. Did you mean @raise?
@param tag has unknown parameter name: options. Did you mean `new_options`?
```
* Rephrased and cleaned up messages.

<details><summary>`yard-junk` tool output</summary>

```
Problems
--------
mistyped tags or other typos in documentation

changeset/lib/rom/changeset.rb:79: [UnknownParam] @param tag has unknown parameter name: options. Did you mean `new_options`?
changeset/lib/rom/changeset/stateful.rb:219: [UnknownParam] @param tag has unknown parameter name: assoc
core/lib/rom/associations/definitions/abstract.rb:66: [UnknownParam] @param tag has unknown parameter name: options
core/lib/rom/attribute.rb:339: [MissingParamName] @param tag has empty parameter name
core/lib/rom/command_registry.rb:52: [UnknownParam] @param tag has unknown parameter name: name
core/lib/rom/commands/class_interface.rb:78: [UnknownParam] @param tag has unknown parameter name: command
core/lib/rom/commands/class_interface.rb:79: [UnknownParam] @param tag has unknown parameter name: parent
core/lib/rom/commands/class_interface.rb:108: [UnknownParam] @param tag has unknown parameter name: options. Did you mean `_options`?
core/lib/rom/commands/class_interface.rb:118: [MissingParamName] @param tag has empty parameter name
core/lib/rom/configuration.rb:46: [UnknownParam] @param tag has unknown parameter name: The
core/lib/rom/configuration.rb:47: [UnknownParam] @param tag has unknown parameter name: Plugin. Did you mean `plugin`?
core/lib/rom/gateway.rb:171: [UnknownParam] @param tag has unknown parameter name: Transaction
core/lib/rom/global.rb:40: [InvalidTagFormat] Invalid tag format for @example
core/lib/rom/global/plugin_dsl.rb:41: [UnknownParam] @param tag has unknown parameter name: adapter
core/lib/rom/memory/dataset.rb:54: [UnknownParam] @param tag has unknown parameter name: names
core/lib/rom/plugin_base.rb:38: [UnknownParam] @param tag has unknown parameter name: base. Did you mean `_base`?
core/lib/rom/plugin_registry.rb:140: [UnknownTag] Unknown tag @raises. Did you mean @raise?
core/lib/rom/plugin_registry.rb:187: [UnknownTag] Unknown tag @raises. Did you mean @raise?
core/lib/rom/relation.rb:297: [UnknownParam] @param tag has unknown parameter name: options
core/lib/rom/relation.rb:406: [UnknownParam] @param tag has unknown parameter name: new_options
core/lib/rom/relation.rb:524: [UnknownParam] @param tag has unknown parameter name: klass
core/lib/rom/relation/combined.rb:28: [MissingParamName] @param tag has empty parameter name
core/lib/rom/relation/curried.rb:69: [UnknownTag] Unknown tag @raises. Did you mean @raise?
core/lib/rom/relation/loaded.rb:91: [UnknownTag] Unknown tag @raises. Did you mean @raise?
core/lib/rom/schema.rb:144: [MissingParamName] @param tag has empty parameter name
core/lib/rom/schema.rb:300: [MissingParamName] @param tag has empty parameter name
core/lib/rom/schema.rb:311: [MissingParamName] @param tag has empty parameter name
core/lib/rom/types.rb:1: [UnknownNamespace] namespace Coercible is not recognized
core/lib/rom/types.rb:1: [UnknownNamespace] namespace Coercible is not recognized
core/lib/rom/types.rb:1: [UnknownNamespace] namespace Coercible is not recognized
mapper/lib/rom/header.rb:47: [UnknownParam] @param tag has unknown parameter name: model
mapper/lib/rom/processor/transproc.rb:212: [MissingParamName] @param tag has empty parameter name

0 failures, 32 problems (2 seconds to run)
```
</details>

It is basically the same as above, and:

* sorted by files/lines instead of "reported when found" approach;
* with short stats at the end;
* returning proper exit code (0 if no problems/parsing errors, non-0 otherwise), which allows `yard-junk`
  to be integrated into CI pipeline, and control that new PRs will not screw docs (forgetting to
  rename parameters in docs when they are renamed in code, for example).

As a nice addition, `yard-junk` command uses its own links to code objects resolver, which is 10x
faster (and, eventually, more correct) than YARD's own approach to resolve links when rendering docs.

## Usage

It is a `yard-junk` gem, install it as usual, or add to your `Gemfile`.

### Better logs

Add this to your `.yardopts` file:
```
--plugin junk
```

After that, just run `yard` or `yard doc` as usual, and enjoy better logs! You can also setup JunkYard
logs by passing options (in the same `.yardopts`):
```
--junk-log-format FORMAT_STR
--junk-log-ignore ERROR_TYPE1,ERROR_TYPE2,...
```

Format is usual Ruby's [#format](https://ruby-doc.org/core-2.2.3/Kernel.html#method-i-format) method
with named fields:
* `message` -- error message;
* `file` -- error file;
* `line` -- error line;
* `type` -- error type.

Default format is `%{file}:%{line}: [%{type}] %{message}`, as shown above.

`--junk-log-ignore` option allows to ingore error classes by their type names (shown in logs in `[]`).
By default, `Undocumentable` error is ignored: it is produced as metaprogramming pieces of code like
```ruby
attr_reader *OPTIONS
```
or
```ruby
include Rails.routes
```
...and typically have no way to fix, while polluting logs with a lot of, well, junk.

### Standalone docs check

Just run `yard-junk` command after gem is installed. Optionally, you can setup "formatters" to use:

* text formatter: suitable for console, sparse colorized output;
* HTML formatter: suitable as CI artifact, readable in browser.

Examples:

* `yard-junk` (default run, outputs text to STDOUT);
* `yard-junk --text` (same as above);
* `yard-junk --text logs/yard.log` (set the output path);
* `yard-junk --text --html build-artifacts/junk-yard.html` (several formatters at once: text to console,
  HTML to file).

You can also specify pathes to report (useful when working on large codebases, when you want to check
only your recent piece of work):

```
yard-junk --path some/path/
yard-junk --path other/path/*sample*.rb
yard-junk --path specific/path.rb
yard-junk --path several,different/*.rb,patterns.rb
```

Note that `yard-junk` would parse the pathes that set in `.yardopts` as usually, and then
**filter report** by pattern specified.

### Rake task (integrating in CI)

Add this to your `Rakefile`:

```ruby
require 'yard-junk/rake'
YardJunk::Rake.define_task
```

and then run it (or add to your `.travis.yml`) as
```
rake yard:junk
```

The Rake task also takes formatter arguments, at task-definition time:

```ruby
YardJunk::Rake.define_task(:text) # default
YardJunk::Rake.define_task(text: 'logs/yard.log') # text to file
YardJunk::Rake.define_task(:text, html: 'build-artifacts/junk-yard.html') # text to STDOUT, html to file
```

## Reasons

Small problems in docs lead to a decrease in readability and usability. But it is hard to check for
all those problems manually due to YARD's cumbersome output, and lack of CI-ready doc checking tools.

The idea of a regularly structured logger was initially [proposed](https://github.com/lsegal/yard/issues/1007)
as an enhancement for YARD itself, and even some steps were made by YARD's author in that direction,
but the idea was abandoned since.

Therefore, this independent tool was made.

## Caveats

Sometimes YARD doesn't provide enough information to guess in which line of code the problem is;
in those cases `yard-junk` just writes something like `file.rb:1` (to stay consistent and not break
go-to-file tools).

## Roadmap

* Docs for usage as a system-wide YARD plugin;
* Docs for internals;
* Documentation quality checks as a next level of YARD checker ([#14](https://github.com/zverok/yard-junk/issues/14)).

## Some examples of problems found in popular gems:

**NB: All of those are excellent libs! The showcase is of "how hard it is to maintain docs quality",
not of "how ignorant other programmers are".**

<details><summary>httparty: 2</summary>

```
lib/httparty/exceptions.rb:2: [UnknownTag] Unknown tag @abstact. Did you mean @abstract?
lib/httparty/exceptions.rb:20: [MissingParamName] @param tag has empty parameter name
```
</details>

<details><summary>vcr: 7</summary>

```
lib/vcr/deprecations.rb:71: [UnknownParam] @param tag has unknown parameter name: name
lib/vcr/deprecations.rb:73: [UnknownParam] @param tag has unknown parameter name: options
lib/vcr/linked_cassette.rb:12: [UnknownParam] @param tag has unknown parameter name: context-owned
lib/vcr/linked_cassette.rb:13: [UnknownParam] @param tag has unknown parameter name: context-unowned
lib/vcr/linked_cassette.rb:55: [UnknownParam] @param tag has unknown parameter name: context-owned
lib/vcr/linked_cassette.rb:56: [UnknownParam] @param tag has unknown parameter name: context-unowned
lib/vcr/test_frameworks/cucumber.rb:27: [UnknownParam] @param tag has unknown parameter name: options
```
</details>

<details><summary>eventmachine: 19</summary>

```
lib/em/channel.rb:39: [UnknownParam] @param tag has unknown parameter name: Subscriber
lib/em/connection.rb:603: [InvalidLink] Cannot resolve link to Socket.unpack_sockaddr_in from text: {Socket.unpack_sockaddr_in}
lib/em/connection.rb:726: [InvalidLink] Cannot resolve link to EventMachine.notify_readable from text: {EventMachine.notify_readable}
lib/em/connection.rb:726: [InvalidLink] Cannot resolve link to EventMachine.notify_writable from text: {EventMachine.notify_writable}
lib/em/connection.rb:739: [InvalidLink] Cannot resolve link to EventMachine.notify_readable from text: {EventMachine.notify_readable}
lib/em/connection.rb:739: [InvalidLink] Cannot resolve link to EventMachine.notify_writable from text: {EventMachine.notify_writable}
lib/em/protocols/httpclient2.rb:263: [InvalidLink] Cannot resolve link to |response| from text: {|response| puts response.content }
lib/em/protocols/httpclient2.rb:276: [InvalidLink] Cannot resolve link to |response| from text: {|response| puts response.content }
lib/em/protocols/line_protocol.rb:9: [InvalidLink] Cannot resolve link to line from text: {line}
lib/em/protocols/object_protocol.rb:9: [InvalidLink] Cannot resolve link to 'you from text: {'you said' => obj}
lib/em/protocols/smtpclient.rb:138: [InvalidLink] Cannot resolve link to "Subject" from text: {"Subject" => "Bogus", "CC" => "<a href="mailto:myboss@example.com">myboss@example.com</a>"}
lib/em/protocols/smtpclient.rb:138: [InvalidLink] Cannot resolve link to :type=>:plain, from text: {:type=>:plain, :username=>"<a href="mailto:mickey@disney.com">mickey@disney.com</a>", :password=>"mouse"}
lib/em/protocols/smtpserver.rb:435: [InvalidLink] Cannot resolve link to :cert_chain_file from text: {:cert_chain_file => "/etc/ssl/cert.pem", :private_key_file => "/etc/ssl/private/cert.key"}
lib/em/protocols/socks4.rb:13: [InvalidLink] Cannot resolve link to data from text: {data}
lib/em/spawnable.rb:47: [InvalidLink] Cannot resolve link to xxx from text: {xxx}
lib/eventmachine.rb:215: [InvalidLink] Cannot resolve link to EventMachine.stop from text: {EventMachine.stop}
lib/eventmachine.rb:231: [InvalidLink] Cannot resolve link to EventMachine::Callback from text: {EventMachine::Callback}
lib/eventmachine.rb:319: [UnknownParam] @param tag has unknown parameter name: delay
lib/eventmachine.rb:345: [UnknownParam] @param tag has unknown parameter name: delay
```
</details>

<details><summary>addressable: 8</summary>

```
lib/addressable/template.rb:197: [UnknownParam] @param tag has unknown parameter name: *indexes. Did you mean `indexes`?
lib/addressable/uri.rb:296: [UnknownParam] @param tag has unknown parameter name: *uris. Did you mean `uris`?
lib/addressable/uri.rb:1842: [UnknownParam] @param tag has unknown parameter name: The
lib/addressable/uri.rb:1943: [UnknownParam] @param tag has unknown parameter name: The
lib/addressable/uri.rb:1958: [UnknownParam] @param tag has unknown parameter name: The
lib/addressable/uri.rb:2023: [UnknownParam] @param tag has unknown parameter name: The
lib/addressable/uri.rb:2244: [UnknownParam] @param tag has unknown parameter name: *components. Did you mean `components`?
lib/addressable/uri.rb:2275: [UnknownParam] @param tag has unknown parameter name: *components. Did you mean `components`?
```
</details>

<details><summary>hashie: 16 (mostly not escaped code in docs)</summary>

```
lib/hashie/extensions/coercion.rb:68: [UnknownParam] @param tag has unknown parameter name: key
lib/hashie/extensions/coercion.rb:69: [UnknownParam] @param tag has unknown parameter name: into
lib/hashie/extensions/deep_find.rb:7: [InvalidLink] Cannot resolve link to user: from text: {user: {location: {address: '123 Street'}
lib/hashie/extensions/deep_find.rb:7: [InvalidLink] Cannot resolve link to user: from text: {user: {location: {address: '123 Street'}
lib/hashie/extensions/deep_find.rb:16: [InvalidLink] Cannot resolve link to location: from text: {location: {address: '123 Street'}
lib/hashie/extensions/deep_find.rb:16: [InvalidLink] Cannot resolve link to location: from text: {location: {address: '123 Street'}
lib/hashie/extensions/deep_find.rb:27: [InvalidLink] Cannot resolve link to users: from text: {users: [{location: {address: '123 Street'}
lib/hashie/extensions/deep_find.rb:27: [InvalidLink] Cannot resolve link to users: from text: {users: [{location: {address: '123 Street'}
lib/hashie/extensions/deep_find.rb:36: [InvalidLink] Cannot resolve link to location: from text: {location: {address: '123 Street'}
lib/hashie/extensions/deep_find.rb:36: [InvalidLink] Cannot resolve link to location: from text: {location: {address: '123 Street'}
lib/hashie/extensions/deep_find.rb:36: [InvalidLink] Cannot resolve link to location: from text: {location: {address: '234 Street'}
lib/hashie/extensions/deep_find.rb:36: [InvalidLink] Cannot resolve link to location: from text: {location: {address: '234 Street'}
lib/hashie/extensions/deep_find.rb:36: [InvalidLink] Cannot resolve link to location: from text: {location: {address: '234 Street'}
lib/hashie/extensions/deep_find.rb:36: [InvalidLink] Cannot resolve link to location: from text: {location: {address: '234 Street'}
lib/hashie/mash.rb:32: [InvalidLink] Cannot resolve link to :a from text: {:a => {:b => 23, :d => {:e => "abc"}
lib/hashie/mash.rb:32: [InvalidLink] Cannot resolve link to :g from text: {:g => 44, :h => 29}
```
</details>

## Authors

* [Victor Shepelev](https://github.com/zverok)
* [Olle Jonsson](https://github.com/olleolleolle)

## License

MIT
