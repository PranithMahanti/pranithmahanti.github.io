---
    layout:     post
    title:      Chatting using the Linux Terminal using IRC
    date:       2025-01-21 00:00:05
    summary:    Because who needs fancy apps when you've got the command line?
    categories: linux
---

We are going to look at how we can chat using Linux Terminal. We will use a text-based chat system called "Internet Relay Chat" or IRC[^1] for this job.

## What is IRC?
Internet Relay Chat (IRC) is an application layer protocol that facilitates communication in the form of text. The chat process works on a client/server networking model. IRC clients are computer programs that users can install on their system or web based applications running either locally in the browser or on a 3rd party server.  
These clients communicate with chat servers to transfer messages to other clients. IRC is mainly designed for *group communication* in discussion forums, called **channels**, but also allows one-on-one communication via *private messages* as well as chat and data transfer, **including file sharing**.

## Installing required packages
The package we need to install is ```irssi```.

- For Debian/Ubuntu based distros:

{% highlight bash lineanchors %}
$ sudo apt-get install irssi
{% endhighlight %}

- For Fedora based distros:

{% highlight bash lineanchors %}
$ dnf install irssi
{% endhighlight %}

- For CentOS/RHEL based distros:

{% highlight bash lineanchors %}
$ yum install irssi
{% endhighlight %}

- For Arch Linux distro:

{% highlight bash lineanchors %}
$ pacman -s irssi
{% endhighlight %}

## Running IRSSI
You can now start irssi by typing ```irssi``` in the command line and hitting enter.

{% highlight bash lineanchors %}
$ irssi
{% endhighlight %}

A screen with the cursor at the bottom can be seen, as shown below:

![irssi]({{ site.baseurl }}/images/irssi)

Now you will have to connect to a server. Some server services are freely available to all, such as *Freenode*.

Enter the below command to connect to the *Freenode* server:

{% highlight bash lineanchors %}
[(status)]  /connect Freenode
{% endhighlight %}

It will connect to the server within a few seconds. And then you will have to join a channel:

{% highlight bash lineanchors %}
[(status)]  /join #TestChannel
{% endhighlight %}

Here, ***TestChannel*** must be replaced by the channel name you want to connect to. This will connect to the channel and then we can start chatting to others on the same channel.

> #### Extra Tip
>
> You can nickname yourself to any name you like using the ```\nick``` command and typing in your desired nickname.

## Additional Resources
---
### 1. Networks
   A collection of IRC servers is known as a **Network**.  
   Here is a curated list of Networks to check out:
   - [Libera.Chat](https://libera.chat/): Network mostly focused on free and open source projects, run by former freenode staff.
   - [Soonet](https://snoonet.org/): Community of redditors and subreddits.
   - [OFTC](https://oftc.net/): Community for free and open source software communities.
   - [LibertaCasa](https://liberta.casa/): A community with multiple interconnected services which provides a safe space for the discussion and dissemination of various topics under the umbrella of Science, Philosophy, Politics.


### 2. A How-to Guide
- [#irchelp](https://www.irchelp.org/): A vast amount of reasonably up-to-date information.

### 3. About the Protocol
Information and resources about the IRC protocol itself.
- [IRCv3 Working Group](https://ircv3.net/): A group of IRC software authors working to enhance, improve, maintain and standardize the IRC protocol.
- [Modern IRC Documents](https://modern.ircdocs.horse/): An attempt to write an update to the original IRC protocol.  
  
  
Happy texting :)

---
### Footnotes:
[^1]: Check out the [Wiki](https://en.wikipedia.org/wiki/IRC)




