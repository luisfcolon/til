# Supress pushd and popd output

If you have a bash script that has ton of processing and heavily use the `pushd` and `popd` commands to switch directories - it will output everytime each one is called.

`pushd` will print the directory we are going to and the current directory.

```
~/Workspace/projects/tutorials/til/unix
$ pushd ~/Downloads
~/Downloads ~/Workspace/projects/tutorials/til/unix

~/Downloads
$
```

`popd` will display the directoy we are going back to

```
~/Downloads
$ popd
~/Workspace/projects/tutorials/til/unix

~/Workspace/projects/tutorials/til/unix
$
```

That can be annoying if you perform those calls enough times. In those types of bash scripts I like to supress the output, temporarily, while the script runs.

```bash
#!/usr/bin/env bash

pushd() {
  command pushd $@ > /dev/null
}

popd() {
  command popd $@ > /dev/null
}

# the code we are executing here

unset -f pushd
unset -f popd
```

* Create a function that overrides the system command
* Call the default system command and send the output to `/dev/null`
* Run the code
* Remove the override functions to restore default functionality