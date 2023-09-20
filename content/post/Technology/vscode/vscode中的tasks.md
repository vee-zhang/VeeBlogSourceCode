# Task中的属性

- label:任务名，会展示出来供用户选择。
- type：任务类别。对于一个自定义的task，这里可以是`shell`或者`process`。如果指定为shell，则command会被解释为shell指令（比如bash,cmd,PowerShell）；如果指定为process，command会被解释为一个进程去执行。
- command：实际要执行的指令。
- windows：Windows系统的特殊参数，可以在使用windows系统时用来替换默认的参数。实际就可以靠这个属性来达到不同系统不同指令的效果。
- group：定义任务的归属，任务分组后，可以直接执行一组任务。
- presentation：定义任务如何输出打印在用户界面。
- options：重写默认`cwd`（current working directory），`env`、`shell`。
- runOptions：定义任务何时、如何执行。