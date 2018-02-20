# sandsifter-tests
A repository of result for runs of sandsifter on various x86 CPU's

## Alert
Due to a recently found fault in the way the injector was compiled all but two test results stopped prematurely at the below instructions:
 * 660f1fff
 * 660f8fff000000

In particular `660fa4c412f900000000000000000000` is what triggered an eventual segfault. I have not yet looked into the full details.

> This primarily affected Intel CPU's - this means that all Intel CPU submissions would have to be retested. The old results can be found in the invalid_tests branch.

## Pull Requests with your logs welcome!

Make sure your submissions are compressed with
```
tar c data/log | xz -9 > brand_model-modelnumber.tar.xz
```

Rename files to match the following standard pattern:

    `{vendor}_{type}-{model}.tar.xz`
    
    Complex type names should use `-` dashes to separate words.
    Underscore should only be used once after the vendor prefix.

## Source code with fixes

https://github.com/rigred/sandsifter


### Test command:

Be sure your terminal has xterm colors set and is as large as you can make it. 80x40 should suffice.
```
export TERM='xterm-256color'
```

Then run the test with the following command
```
./sifter.py --unk --dis --len --sync --tick -- -P1 -t
```

### Compression
> Log data is compressed With xz -9 and will uncompress to a good bit larger size
Special attention is needed with the Ryzen CPU test data. The dump files for those are near 1.4Gb total when uncompressed. 
Running this through the analysis tool will consume a substantial amount of RAM.

## CPU's tested:

### AMD

* Zen (Summit Ridge)
    ## Microcode 1129
    * [R7 1700x](amd/amd_ryzen-1700x-uc1129.tar.xz)
    * [R7 1700](amd/amd_ryzen-1700-uc1129.tar.xz)
    ## Microcode 1126
    * [R7 1700x](amd_ryzen-1700x-uc1126.tar.xz)

    *Warning:* The Zen CPU logs are ***LARGE***. 
    > Processing these with the summarizer requires a substantial amount of RAM and CPU time.

### Intel

* Dothan
    * [Intel Celeron M 390](intel/intel_celeron-M-390.tar.xz)

* Prescott
    * [Intel Pentium 4 630](intel/intel_pentium-4-630.tar.xz)
    
* Conroe
    * [Intel Celeron 430](intel/intel_celeron-430.tar.xz)
    * [Intel Core 2 Duo E6300](intel/intel_core-2-duo-e6300.tar.xz)
    
* Kentsfield
    * [Core2Quad Q6600](intel/intel_core-2-quad-Q6600.tar.xz)

* Sandy Bridge
    * [Pentium B970](intel/intel_pentium-B970.tar.xz)
    * [Core i5-2500](intel/intel_i5-2500.tar.xz)
    * [Core i5-2540M](intel/intel_i5-2540M.tar.xz)

* Ivy Bridge
    * [Core i3-3120m](intel/intel_i3-3120M.tar.xz)
    
* Haswell
    * [Core i7-4702MQ](intel/intel_i7-4702MQ.tar.xz)
    * [E3-1225 v3](intel/intel_xeon-E3-1225-v3.tar.xz) Ubuntu VM on an ESXI host

* Devil's Canyon
    * [i7-4790k](intel/intel_i7-4790K.tar.xz)
    
* Kaby Lake
    * [Xeon E3-1505M v6](intel/intel_xeon-E3-1505M-v6.tar.xz)

    
## [Credits for CPU test submissions to:](CONTRIBUTORS.md)

* [Lewiscowles1986](https://github.com/Lewiscowles1986)
* [jotebe](https://github.com/jotebe)
* [killerkalamari](https://github.com/killerkalamari)
* [helospark](https://github.com/helospark)
* [Maxzor](https://github.com/Maxzor)
* [Terraflux](https://github.com/Terraflux)
* [wouterwashere](https://github.com/wouterwashere)

Submissions always welcome!
