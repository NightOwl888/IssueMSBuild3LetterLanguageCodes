MSBuild 3-Letter Language Code Issue
=====================

This is a repro demonstrating that MSBuild does not copy resource files with 3-letter language codes to the build/publish output.

1. Build ProjectA. It will create a ProjectA.1.0.0.nupkg file in the repo root.
2. Check the contents of ProjectA.1.0.0.nupkg. Both `en` and `agq` languages are present, as expected.
2. Build ProjectB.
3. Check the build output. Only `en` is present, `agq` is not.

We are also seeing this occur with `dotnet publish` and with the`PackAsTool` option.

The following neutral cultures are confirmed to be failing:

agq
ars
asa
ast
bas
bem
bez
brx
ccp
cgg
chr
ckb
dav
dje
dsb
dua
dyo
ebu
ewo
fil
fur
gsw
guz
haw
hsb
jgo
jmc
kab
kam
kde
kea
khq
kkj
kln
kok
ksb
ksf
ksh
lag
lkt
lrc
luo
luy
mas
mer
mfe
mgh
mgo
mua
mzn
naq
nds
nmg
nnh
nus
nyn
qu
rof
rwk
sah
saq
sbp
seh
ses
shi
shi-Latn
shi-Tfng
smn
teo
twq
tzm
vai
vai-Latn
vai-Vaii
vun
wae
xog
yav
zgh

Presumably, the specific variants are also failing, but we haven't confirmed.