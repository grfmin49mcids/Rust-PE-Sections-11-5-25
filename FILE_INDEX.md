# every file explained

## gameassembly

GameAssembly.dll dumped off disk. this is the il2cpp build, all the managed game code compiled to native

**headers.bin** : pe headers (256 bytes)

**text.bin** : .text section, the code, 7.9mb

**il2cpp.bin** : the .il2cpp section, 196mb. the giant generated il2cpp code section, biggest part of the dll

**rdata.bin** : .rdata, 32mb of strings vtables and imports. all the il2cpp baselib symbols are in here

**pdata.bin** : .pdata, 7.8mb of unwind info

**data.bin** : .data, 12mb of globals

**reloc.bin** : .reloc, 3.7mb of base relocations

**fptable.bin** : 512 bytes of function pointers

## gamemem

GameAssembly.dll dumped from memory while the game is running. same sections, same sizes, different bytes. this is the loaded version so relocations are applied and the data is initialized

**headers.bin** : pe headers, identical to the disk one

**text.bin** : .text as it sits in memory, 7.9mb

**il2cpp.bin** : .il2cpp in memory, 196mb

**rdata.bin** : .rdata in memory, 32mb

**pdata.bin** : .pdata, 7.8mb

**data.bin** : .data initialized, 12mb

**reloc.bin** : .reloc, 3.7mb

**fptable.bin** : 512 bytes of function pointers

## rustdisk

RustClient.exe off disk. its just a small launcher stub, manifest pulls in unityplayer

**headers.bin** : pe headers

**text.bin** : .text, 52k of code

**rdata.bin** : .rdata, 38k of strings and imports

**rsrc.bin** : .rsrc, 552k. resources and the manifest that references UnityPlayer

**pdata.bin** : .pdata, 4k

**reloc.bin** : .reloc, 2k

**data.bin** : .data, 3k

## rustmem

RustClient.exe from memory. code differs from the disk version so u can see what changed on load

**headers.bin** : pe headers

**text.bin** : .text in memory, 52k

**rdata.bin** : .rdata in memory, 38k

**rsrc.bin** : .rsrc, 552k

**pdata.bin** : .pdata, 4k

**reloc.bin** : .reloc, 2k

**data.bin** : .data, 3k

## unitymem

UnityPlayer.dll dumped from memory. the whole unity engine

**headers.bin** : pe headers

**text.bin** : .text, 29mb of engine code

**rdata.bin** : .rdata, 4.9mb. full of unity source paths, shader names, enlighten files

**rdatax.bin** : extra rdata section, 68k

**rodata.bin** : .rodata, 3k

**data.bin** : .data, 350k

**reloc.bin** : .reloc, 147k

**pdata.bin** : .pdata, 1.3mb of unwind info

**rsrc.bin** : .rsrc, 2.5k
