# Overview
You should be able to use SPMC without needing to change the default network settings.

If you have an advanced settop box such as an NVIDIA Shield TV or Amazon Fire TV, then you can take advantage of its Gigabit Ethernet port or Wireless AC (5Ghz channel only) connectivity and relatively large memory to locally buffer more of high bitrate videos on your settop box. 

You can then confirm how much local buffer is being used by invoking **codecinfo** within SPMC.

# SPMC Settings
```
<advancedsettings>
	<network>
   		<buffermode>1</buffermode> <!-- Buffer all filesystems (including local)  -->
   		<cachemembuffersize>209715200</cachemembuffersize> --> <!-- 200MB buffer  -->
	    <readbufferfactor>20</readbufferfactor>
	</network>
</advancedsettings>
```