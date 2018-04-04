# rPi-xmrig-gcc7.3.0
## The fastest miner available for Raspbian on Raspberry Pi.
*Updated to 2.6.0-beta1 for Aeon, XMR and Sumo PoW changes* - cryptonight-heavy support

This miner is a compilation of https://github.com/xmrig/xmrig version 2.6.0-beta1, compiled with gcc/g++ 7.3.0 specifically for Raspbian Jessie on Raspberry Pi3 b (untested on earlier models - but please feel free to try and post your findings). As noted in the Ubuntu build instructions on the official xmrig repo: "Optionally you can use gcc 7 to small performance increase" (https://github.com/xmrig/xmrig/wiki/Ubuntu-Build). Additionally, a recent change _might_ take further advantage of 7.3.0 over 7.1.0, seen discussed here: https://github.com/xmrig/xmrig/pull/385. **TL;DR - use this binary for a 15%-20% performance boost on Raspbian.**

## So what?

The latest version of gcc/g++ available from Raspbian repositories is 6.1.0, and you will be hard-pressed to find a third party binary for 7+ at the moment. To solve this, I compiled 7.3.0 from source, directly on one of my rPi3's (long process- saving you time here!). Then, after making a slight tweak to the flags.cmake file from the original xmrig repo, I was able to successfully compile xmrig 2.6.0-beta1 with gcc-7.3.0:

![init gcc-7.3.0](https://i.imgur.com/CV3gvNU.png)

## Results

I now see an approximate 20% hashrate increase with my new xmrig binary! I tested the binary on two other rPi3b's I have and saw the same performance boost. My pi's have heatsinks, fans and mild overclocks (cpu_freq=1325, sdram_freq=500). Mining **Aeon** with the gcc 6.1.0 xmrig binary, I average ~21.8 H/s. With the new 7.3.0 xmrig binary, I'm averaging ~25.1 H/s!

![hashrate gcc-7.3.0](https://i.imgur.com/84csjI4.png)

## Usage

Usage is the same as xmrig-v2.6.0-beta1: https://github.com/xmrig/xmrig/tree/v2.6.0-beta1#usage

## Warning

I DO NOT RECOMMEND that anyone ever download binaries/executables from third party sources or unofficial Github repos. You can review my credits section to see my sources, and really just take me at my word from there. Hopefully some brave users will try it out and report back here to vouch for me :)

## Donations

I have not altered, or reduced the default xmrig donations in my compilations, as I respect the work that the developers have put in, I'm merely standing (crouching?) on their shoulders. However, if you feel like giving me a small donation for my time spent and sharing this binary and my findings, please feel free to donate to one of my wallets:
* xmr: 4BrL51JCc9NGQ71kWhnYoDRffsDZy7m1HUU7MRU4nUMXAHNFBEJhkTZV9HdaL4gfuNBxLPc3BeMkLGaPbF5vWtANQuJBHa28DsCLY6LkxP
* aeon: WmsqiMAQtMHCLs1XzCm7bL6aAALG7GBaGW2CfPF6X9L7hoNZQK3dMsvTMFooCncshGCG2JC6nhFeAcmR1197MKGU2Dojden7k
* sumo: Sumoo3Puf8bAUMqCtmhfeVD48rypZDPCsCVgEe3mGp5FXQC8vcV3n2wV53hKNYbknHSfCeEC82K2JBFQkPCo3qEMMHpB17MeRux
* trtl: TRTLv3STqeVN3WGh6Je1ikLTsUxejmvqiKo3FaigDQSkSMeGfnY2U8SX92eH7KixU3Mdss59wS2NXXwV7TLstURPWPi6C99aWfT

## Credits
* Official xmrig repo: https://github.com/xmrig/xmrig
* Guide that helped me in compiling gcc on Raspberry Pi: https://solarianprogrammer.com/2017/12/07/raspberry-pi-raspbian-compiling-gcc/

## Performance notes/known issues
* Max hashrate stat seems to get stuck shortly after starting - no actual impact
* I find --av=3 gives best results
* I suggest using a proxy like xmrig-proxy if you plan to cluster some pi's for mining: https://github.com/xmrig/xmrig-proxy
* I _definitely_ see better performance (~10%) when the display goes blank/to sleep. Not sure why, since I seem to get the same behavior whether I boot to desktop or CLI (happens with 6.1.0 gcc too- not specific to this build. Just an rPi oddity i've noticed).
