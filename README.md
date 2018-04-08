# bodymovin_fix

-2018.04.08 update ->[5.1.10](https://raw.githubusercontent.com/bigxixi/bodymovin_cn/master/5.1.10/bodymovin5.1.10en_pngfixed.zxp)   

Fix the 'png dark outline' issue.  
The fixed zxp file [Download here](https://github.com/bigxixi/bodymovin_fix/raw/master/bodymovin5.1.9_fixed.zxp)(v5.1.9). 
Use the downloaded file to reinstall bodymovin, I recommand you use https://aescripts.com/learn/zxp-installer/  

# about the fix tool
I uplaod the fix tool(for Mac), if bodymovin updates in the future, this tool may help fix the problem in new versions.  
1. Download the files, unzip the '[Mac]pngFixTool(fix_and_ZXP_repack).zip'.
2. Run Terminal, type in 'chmod +x ' then drag the pngFixTool.command to terminal. Hit ENTER.
3. Now you can double click the pngFixTool.command, or just drag it to the terminal, hit ENTER, to execute it.
4. Drag bodymovin.zxp to the terminal, hit ENTER.
<img src="https://github.com/bigxixi/bodymovin_fix/raw/master/howto.gif" width="50%" />
If everything goes well, a bodymovin_fixed.zxp will be generated next to the original one.
Now install the fixed bodymovin(I recommand you use https://aescripts.com/learn/zxp-installer/), 
then run AE, try export an animation through bodymovin with png asset, check if the dark outline is gone. 

# about the 'png dark outline' issue
Bodymovin uses an undocumented function `saveFrameToPng()` to generate pngs.   
see: https://github.com/bodymovin/bodymovin-extension/blob/16c2ba27a5b0fcaf5a0f043d7c2704259661f3eb/bundle/jsx/utils/sourceHelper.jsx#L145  

But this method exports pngs not premultiplied(with black matt), if the png has alpha channel, it will looks like there are black outlines around the edges.   
If we export pngs through Render Queue, there won't be any unnecessary black outlines.  
So I [write a script function](https://gist.github.com/bigxixi/d65f46552f8d1c2b91a8638f018f1843) to do that, and replace the `saveFrameToPng()` in bodymovin, repack the zxp.  
I've run some test and everything seems OK, if you suffer form this issue, just have a try.  
I hope it helps.

</br>

**PNG through Render Queue**  
![](https://raw.githubusercontent.com/bigxixi/ReadMe-Resources/master/SaveFrameAsPNG-Plus/goodalpha1.png)  

**PNG through `saveFrameToPng()`**  
![](https://raw.githubusercontent.com/bigxixi/ReadMe-Resources/master/SaveFrameAsPNG-Plus/badalpha1.png)
</br>
## Donation:

Thank you very much!  

[<img src="http://bigxixi.com/donate/index.hyperesources/paypal.png" width="30%" height="30%">](https://www.paypal.me/bigxixi/)  
