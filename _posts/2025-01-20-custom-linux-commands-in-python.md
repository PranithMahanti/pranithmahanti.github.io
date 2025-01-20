---
    layout:     post
    title:      Creating custom commands in Linux using Python
    date:       2020-05-08 11:21:29
    summary:    You can now easily automate your workflow and have fun!
    categories: jekyll pixyll
---

Did you know that you can build your own custom commands for your Linux terminal using Python? Or any programming language for that matter?  

  
That's right! And this is how it looks:  

{% highlight bash lineanchors %}
$ multiply 2 14
{% endhighlight %}
Imagine we have a script ```multiply.py``` with the code as below:  
{% highlight bash lineanchors %}
import sys
print(sys.argv[1]*sys.argv[2]) #This outputs the multiply of the number
{% endhighlight %}
If you run this command you can see the following output:  
{% highlight bash lineanchors %}
$ python3 multiply.py 20 4
80
{% endhighlight %}
Now we have just three steps to do…

### Mark your Python file as executable
You can mark your file as executable by running ```chmod``` command.  

{% highlight bash lineanchors %}
$ chmod +x multiply.py
{% endhighlight %}

Now the script can be easily run by using the command:

{% highlight bash lineanchors %}
$ ./multiply.py 2 74
{% endhighlight %}

We need to prefix our command with ./ because usually the current directory is not included in the ```PATH``` environment variable on Unix. This “dot slash” prefix is a security feature.

Anyway - we run into a crazy error message if you try to run the script.

{% highlight bash lineanchors %}
./multiply.py: line 3: syntax error near unexpected token 'print'
./multiply.py: line 3:    print(sys.argv[1]*sys.argv[2])
{% endhighlight %}

The reason for that is that now the system doesn’t know it’s supposed to execute a Python script. So instead it takes a wild guess and tries to run your Python script like a shell script with the ```/bin/sh``` interpreter.

### Add a shebang interpreter
You will have to add a line to the code in the first line. It tells the computer to run the script as a Python file. The line to add is:

{% highlight bash lineanchors %}
#!/usr/bin/env python
{% endhighlight %}

After adding this line if you try to run the code it. It will run fine, giving the required output.

Now we need to drop the .py extension. To do this we just have to rename it.

{% highlight bash lineanchors %}
$ mv multiply.py multiply
{% endhighlight %}

Let’s try and run it

{% highlight bash lineanchors %}
$ ./multiply 20 20
400
{% endhighlight %}

Yes. It gave us the required output.

### Make sure your program is on the PATH
The last thing you need to change to make your Python script really seem like a shell command or system tool is to make sure it’s on your ```PATH```.  

I don’t recommend that you try to copy your script to a system directory like ```/usr/bin/``` or ```/usr/local/bin``` because that can lead to all kinds of odd naming conflicts (and, in the worst case, break your operating system install).  

So instead, what you’ll want to do is to create a bin directory in your user’s home directory and then add that to the ```PATH```.

First, you need to create the ```~/bin``` directory:

{% highlight bash lineanchors %}
$ mkdir -p ~/bin
{% endhighlight %}

Next, copy your script to ```~/bin```:

{% highlight bash lineanchors %}
$ cp multiply ~/bin
{% endhighlight %}

Finally, add ```~/bin``` to your ```PATH```:

{% highlight bash lineanchors %}
export PATH=$PATH":$HOME/bin"
{% endhighlight %}

Adding ```~/bin``` to the ```PATH``` like this is only temporary, however. It won’t stick across terminal sessions or system restarts. If you want to make your command permanently available on a system, do the following:

Add the this line to ```.profile``` : ```export PATH=$PATH”:$HOME/bin”```.  
The changes can be observed after the terminal reloads or if you run a new session.  
Now we can use the command that we created. Yay !!!  

{% highlight bash lineanchors %}
$ multiply 20 4
80
{% endhighlight %}

I hope you like this article!!  

Thank you!