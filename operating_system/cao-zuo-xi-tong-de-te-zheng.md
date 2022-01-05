# 操作系统的特征

#### 1. 并发(Concurrence)

并发是指两个或多个事件在 <mark style="color:blue;"></mark> <mark style="color:blue;"></mark><mark style="color:blue;">**同一时间间隔内**</mark> 发生。操作系统的并发性是指计算机系统中同时存在多个运行的程序，因此它具有处理和调度多个程序同时执行的能力。在操作系统中，引入进程的目的是使程序能并发执行。

在多道程序环境下，一段时间内，宏观上有多道程序在同时执行，而在每个时刻，单处理机环境下实际仅能有一道程序执行，因此微观上这些程序仍是分时交替执行的。操作系统的并发性是通过分时得以实现的。

注意，并行性是指系统具有同时进行运算或操作的特性，在同一时刻能完成两种或两种以上的工作。并行性需要有相关硬件的支持，如多流水线或多处理机硬件环境。

<mark style="color:blue;">**并行性是指两个或多个事件在同一时刻发生；而并发性是指两个或多个事件在同一时间间隔内发生。**</mark>

并发和并行的例子：如果你在18:00-18:10看视频，在18:11-18:20吃晚饭，在18:21-18:30看视频，在18:00-18:30这段时间内吃晚饭和看视频两种行为就是并发执行的；但如果你在18:00-18:30这段时间内边吃晚饭边看视频，那么这两个行为就是并行执行的。

#### 2. 共享(Sharing)

资源共享即共享，是指系统中的资源可供内存中多个并发执行的进程共同使用。根据资源性质的不同，可将资源共享方式分为两种：

**(1)互斥共享方式**

系统中可供共享的某些资源，如打印机、某些变量、队列等一段时间内只能供一个作业使用的资源，只有当前作业使用完毕并释放后，才能被其他作业使用。而把在一段时间内只允许一个进程访问的资源称为 <mark style="color:blue;">**临界资源**</mark> 或 <mark style="color:blue;">**独占资源**</mark> 。计算机系统中的大多数物理设备及某些软件中所用的栈、变量和表格，都属于临界资源，它们都要求被互斥地共享。

**(2)同时访问方式**

系统中的另一类资源，如磁盘、可重入代码等，可以供多个作业同时访问。虽然这种“同时”是指宏观上的“同时”，微观上可能是作业交替访问该资源，但作业访问资源的顺序不会影响访问的结果。

<mark style="color:blue;">**并发和共享是操作系统两个最基本的特征**</mark>，两者之间互为存在的条件：

* 资源共享是以程序的并发为条件的，若系统不允许程序并发执行，则自然不存在资源共享问题；
* 若系统不能对资源共享实施有效的管理，则必将影响到程序的并发执行，甚至根本无法并发执行。

#### 3. 虚拟(Virtual)

虚拟是指把一个物理上的实体变为若干逻辑上的对应物。物理实体(前者)是实的，即实际存在的；而后者是虚的，是用户感觉上的事物。用于实现虚拟的技术，称为虚拟技术。操作系统中利用了多种虚拟技术来实现虚拟处理器、虚拟内存和虚拟外部设备等。虚拟处理器技术是通过多道程序设计技术，采用让多道程序并发执行的方法，来分时使用个处理器的。此时，虽然只有一个处理器，但它能同时为多个用户服务，使每个终端用户都感觉有一个中央处理器(CPU)在专门为它服务。利用多道程序设计技术把一个物理上的CPU虚拟为多个逻辑上的CPU，称为虚拟处理器。

类似地，可以采用虚拟存储器技术将一台机器的物理存储器变为虚拟存储器，以便从逻辑上扩充存储器的容量。当然，这时用户所感觉到的内存容量是虚的。我们把用户感觉到(但实际不存在)的存储器称为虚拟存储器。

还可采用虚拟设备技术将一台物理IO设备虚拟为多台逻辑上的IO设备，并允许每个用户占用一台逻辑上的IO设备，使原来仅允许在一段时间内由一个用户访问的设备(即临界资源)变为在一段时间内允许多个用户同时访问的共享设备。因此，操作系统的虚拟技术可归纳为： <mark style="color:blue;">**时分复用技术**</mark> ，如处理器的分时共享； <mark style="color:blue;"></mark> <mark style="color:blue;"></mark><mark style="color:blue;">**空分复用技术**</mark> ，如虚拟存储器。

在操作系统中，虚拟是指把一个物理上的实体变为若干个逻辑上的对应物，前者是实际存在的，后者是虚拟的，这只是用户的一种感觉。例如，在操作系统中引入多道程序设计技术后，虽然只有一个CPU，每次只能执行一道程序，但通过分时使用，在一段时间间隔内宏观上这台处理器能同时运行多道程序。它给用户的感觉是每道程序都有一个CPU为其服务。也就是说，多道程序设计技术可以把一台物理上的CPU虚拟为多台逻辑上的CPU。此外还有虚拟存储器(从逻辑上扩充存储器的容量)、虚拟设备(独占设备变为共享设备)等技术。

#### 4. 异步(Asynchronism)

多道程序环境允许多个程序并发执行，但由于资源等因素的限制，进程的执行并不是一贯到底的，而是“走走停停”的，它以不可预知的速度向前推进，这就是进程的异步性。

异步性使得操作系统运行在一种随机的环境下，可能导致进程产生与时间有关的错误(就像对全局变量的访问顺序不当会导致程序出错一样)。然而，只要运行环境相同，操作系统就须保证多次运行进程后都能获得相同的结果。