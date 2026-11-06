# rust pe section dumps

every section dumped out of what rust loads. got the game exe, the unity engine, and the whole il2cpp gameassembly, in disk and memory versions so u can diff what changes once its running

u can use these to find really crazy exploits with the entire game and go through and use ida to see how every single thing works, engine, physics, ect, enjoy!!!!!!!!!!!!!

## the folders

**gameassembly** : GameAssembly.dll off disk. the big one, all the il2cpp game code, almost 250mb of sections

**gamemem** : GameAssembly.dll dumped straight out of memory while running. same files as the disk dump but live, relocations applied and data initialized. diff it against gameassembly to see what the game changes on load

**rustdisk** : RustClient.exe off disk. tiny launcher stub

**rustmem** : RustClient.exe from memory. diff against rustdisk to see what it does once its loaded

**unitymem** : UnityPlayer.dll from memory. the whole unity engine, d3d12 rendering, enlighten, all of it

## the files in each folder

**headers.bin** : pe headers, image base and where every section goes

**text.bin** : the .text section, the actual code

**rdata.bin** : .rdata, strings vtables imports

**data.bin** : .data, globals and initialized data

**pdata.bin** : .pdata, unwind info, function start and end addresses

**reloc.bin** : .reloc, base relocations

**fptable.bin** : raw function pointers (gameassembly only)

**il2cpp.bin** : the .il2cpp section, 196mb of generated il2cpp code (gameassembly only)

**rsrc.bin** : resources, manifests and version info

**rdatax.bin / rodata.bin** : extra read only sections (unitymem only)

every file is listed in FILE_INDEX.md

## using it

headers.bin has the image base and section rvas. drop each bin at its rva in ida and the module rebuilds itself. gameassembly is where the game logic lives, unitymem is the engine under it, and the disk vs memory pairs show u exactly what gets patched when it loads
