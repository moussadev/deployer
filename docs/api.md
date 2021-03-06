<!-- DO NOT EDIT. Run bin/docgen to update. -->

# API Reference

 * [`host()`](#host)
 * [`localhost()`](#localhost)
 * [`getHost()`](#getHost)
 * [`currentHost()`](#currentHost)
 * [`inventory()`](#inventory)
 * [`desc()`](#desc)
 * [`task()`](#task)
 * [`before()`](#before)
 * [`after()`](#after)
 * [`fail()`](#fail)
 * [`option()`](#option)
 * [`cd()`](#cd)
 * [`within()`](#within)
 * [`run()`](#run)
 * [`runLocally()`](#runLocally)
 * [`test()`](#test)
 * [`testLocally()`](#testLocally)
 * [`on()`](#on)
 * [`invoke()`](#invoke)
 * [`upload()`](#upload)
 * [`download()`](#download)
 * [`info()`](#info)
 * [`warning()`](#warning)
 * [`writeln()`](#writeln)
 * [`write()`](#write)
 * [`parse()`](#parse)
 * [`set()`](#set)
 * [`add()`](#add)
 * [`get()`](#get)
 * [`has()`](#has)
 * [`ask()`](#ask)
 * [`askChoice()`](#askChoice)
 * [`askConfirmation()`](#askConfirmation)
 * [`askHiddenResponse()`](#askHiddenResponse)
 * [`input()`](#input)
 * [`output()`](#output)
 * [`commandExist()`](#commandExist)
 * [`commandSupportsOption()`](#commandSupportsOption)
 * [`locateBinaryPath()`](#locateBinaryPath)

## host()

```php
host(...$hostname)
```


## localhost()

```php
localhost(...$hostnames)
```


## getHost()

```php
getHost(string $alias)
```

Get host by host alias.


## currentHost()

```php
currentHost()
```

Get current host.


## inventory()

```php
inventory($file)
```

Load list of hosts from file


## desc()

```php
desc($title = null)
```

Set task description.


## task()

```php
task($name, $body = null)
```

Define a new task and save to tasks list.

Alternatively get a defined task.


## before()

```php
before($task, $do)
```

Call that task before specified task runs.


## after()

```php
after($task, $do)
```

Call that task after specified task runs.


## fail()

```php
fail($task, $do)
```

Setup which task run on failure of first.


## option()

```php
option($name, $shortcut = null, $mode = null, $description = '', $default = null)
```

Add users options.


## cd()

```php
cd($path)
```

Change the current working directory.


## within()

```php
within($path, $callback)
```

Execute a callback within a specific directory and revert back to the initial working directory.


## run()

```php
run($command, $options = [])
```

Executes given command on remote host.

Options:
- `timeout` - Sets the process timeout (max. runtime). The timeout in seconds (default: 300 sec).
- `secret` - Placeholder `%secret%` can be used in command. Placeholder will be replaced with this value and will not appear in any logs.

Examples:

```php
run('echo hello world');
run('cd {{deploy_path}} && git status');
run('password %secret%', ['secret' => getenv('CI_SECRET')]);
```

```php
$path = run('readlink {{deploy_path}}/current');
run("echo $path");
```


## runLocally()

```php
runLocally($command, $options = [])
```

Execute commands on local machine


## test()

```php
test($command)
```

Run test command.
Example:

```php
if (test('[ -d {{release_path}} ]')) {
...
}
```


## testLocally()

```php
testLocally($command)
```

Run test command locally.
Example:

    testLocally('[ -d {{local_release_path}} ]')


## on()

```php
on($hosts, callable $callback)
```

Iterate other hosts, allowing to call run func in callback.


## invoke()

```php
invoke($task)
```

Run task


## upload()

```php
upload(string $source, string $destination, $config = [])
```

Upload file or directory to host.

> You may have noticed that there is a trailing slash (/) at the end of the first argument in the above command, this is necessary to mean “the contents of build“.
>
> The alternative, without the trailing slash, would place build, including the directory, within public. This would create a hierarchy that looks like: {{release_path}}/public/build


## download()

```php
download(string $source, string $destination, $config = [])
```

Download file or directory from host


## info()

```php
info($message)
```

Writes an info message.

## warning()

```php
warning($message)
```

Writes an warning message.

## writeln()

```php
writeln($message, $options = 0)
```

Writes a message to the output and adds a newline at the end.

## write()

```php
write($message, $options = 0)
```

Writes a message to the output.

## parse()

```php
parse($value)
```

Parse set values.


## set()

```php
set($name, $value)
```

Setup configuration option.


## add()

```php
add($name, $array)
```

Merge new config params to existing config array.


## get()

```php
get($name, $default = null)
```

Get configuration value.


## has()

```php
has($name)
```

Check if there is such configuration option.


## ask()

```php
ask($message, $default = null, $autocomplete = null)
```


## askChoice()

```php
askChoice($message, array $availableChoices, $default = null, $multiselect = false)
```


## askConfirmation()

```php
askConfirmation($message, $default = false)
```


## askHiddenResponse()

```php
askHiddenResponse(string $message)
```


## input()

```php
input()
```


## output()

```php
output()
```


## commandExist()

```php
commandExist($command)
```

Check if command exists


## commandSupportsOption()

```php
commandSupportsOption($command, $option)
```


## locateBinaryPath()

```php
locateBinaryPath($name)
```


