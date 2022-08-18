- Download MCP from http://www.modcoderpack.com/files/mcp940.zip
- Unzip
- https://gist.github.com/Pokechu22/97bf5bd528eeadef09dcbae8a15b009f and use
https://github.com/ModCoderPack/MCPMappingsArchive/tree/master/mcp_stable/39-1.12 for mappings
- `bash decompile.sh`
- In the `jars` folder in MCP it'll copy your entire `.minecraft/assets` folder so keep that in mind. This means it'll copy over every asset file for every version of Minecraft.
I personally symlink my assets folder over.
- Optifine download time: https://optifine.net/adloadx?f=OptiFine_1.12.2_HD_U_G5.jar
- Run as a program and extract.
- Open up the Minecraft jar in jars/versions/1.12.2 and paste in the contents of the MOD Optifine jar you just created. I'm going to call this the MegaJar.
- `bash cleanup.sh`
- `bash decompile.sh` again
- Copy everything in the `jars` folder in this repository to `lib` in the MCP folder.
- Delete the `src/minecraft/optifine` (NOT `src/minecraft/net/optifine`) as these classes are not used for our purposes
- Create a git repository in the MCP directory, add everything in `src/minecraft` and commit
- Apply the patches in this repository - if you add them to the MCP directory then it's probably `git am *.patch`
- Download RetroLambda: https://oss.sonatype.org/content/groups/public/net/orfjackal/retrolambda/retrolambda/
- Create a folder on your PowerPC machine for this madness
- Add an assets folder. For now, the easiest way to get an assets folder is running 1.12.2 on another computer and then copying `.minecraft/assets` to your PowerPC computer.
- Create a libraries folder and add everything from `jars` here, and download all the links and extract/add them there.
- Create a natives folder and copy everything from `natives` here to there.
- Create a startup.sh script that looks something like this:

```sh
MC_MAIN_PATH="/Users/YOUR_NAME_HERE/wherever/you/put/the/folder"; cd "$MC_MAIN_PATH"; java -cp "$MC_MAIN_PATH"/minecraft.jar:"$MC_MAIN_PATH"/libraries/guava-jdk5-17.0.jar:"$MC_MAIN_PATH"/libraries/jinput.jar:"$MC_MAIN_PATH"/libraries/lwjgl.jar:"$MC_MAIN_PATH"/libraries/lwjgl_util.jar:"$MC_MAIN_PATH"/libraries/netty-buffer-4.0.10.Final.jar:"$MC_MAIN_PATH"/libraries/netty-codec-4.0.10.Final.jar:"$MC_MAIN_PATH"/libraries/netty-common-4.0.10.Final.jar:"$MC_MAIN_PATH"/libraries/netty-handler-4.0.10.Final.jar:"$MC_MAIN_PATH"/libraries/netty-transport-4.0.10.Final.jar:"$MC_MAIN_PATH"/libraries/codecjorbis-1.0-SNAPSHOT.jar:"$MC_MAIN_PATH"/libraries/codecwav-20101023.jar:"$MC_MAIN_PATH"/libraries/commons-codec-1.6.jar:"$MC_MAIN_PATH"/libraries/commons-io-2.2.jar:"$MC_MAIN_PATH"/libraries/commons-logging-1.1.3.jar:"$MC_MAIN_PATH"/libraries/jutils-1.0.0.jar:"$MC_MAIN_PATH"/libraries/soundsystem-20120107.jar:"$MC_MAIN_PATH"/libraries/vecmath-1.3.1.jar:"$MC_MAIN_PATH"/libraries/authlib-1.5.21.jar:"$MC_MAIN_PATH"/libraries/log4j-api-2.3.jar:"$MC_MAIN_PATH"/libraries/log4j-to-slf4j-2.3.jar:"$MC_MAIN_PATH"/libraries/jopt-simple-4.6.jar:"$MC_MAIN_PATH"/libraries/gson-2.2.4.jar:"$MC_MAIN_PATH"/libraries/commons-lang3-3.1.jar:"$MC_MAIN_PATH"/libraries/librarylwjglopenal-20100824.jar:"$MC_MAIN_PATH"/libraries/icu4j-core-mojang-51.2.jar:"$MC_MAIN_PATH"/libraries/trove4j-3.0.3.jar:"$MC_MAIN_PATH"/libraries/slf4j-api-1.7.21.jar:"$MC_MAIN_PATH"/libraries/slf4j-simple-1.7.21.jar:"$MC_MAIN_PATH"/libraries/fastutil-7.2.1.jar:"$MC_MAIN_PATH"/libraries/sanselan-0.97-incubator.jar: -Djava.library.path="$MC_MAIN_PATH"/natives/ -Xms768M -Xmx768M net.minecraft.client.main.Main --version mcp --assetsDir "$MC_MAIN_PATH"/assets/ --gameDir . --assetIndex 1.12 --accessToken empty --userProperties {} --username USERNAME
```

Take note that the beginning and end need to be modified for your use-case.

Actually compiling every time:

- `bash recompile.sh`
- Run the retrolambda.sh script here - assuming you're using Retrolambda 2.5.7 it should work out of the box?
- Everything in bin/minecraft/ is the Minecraft output classes. Copy this over to your PowerPC machine however you please
- On your PowerPC machine, ensure that the assets folder and pack.png file inside the MegaJar are copied the folder of your compiled classes. You only have to do this once assuming you don't delete these files.

I've been using Java 8 to handle everything here.

I'm on Linux and I'm so sorry if you're not. PRs welcome to make these instructions more Windows-friendly.

It should be understood here that I am absolutely against piracy using this tool. At this point in time I don't know how
feasible it is to log into Microsoft on a fifteen-year-old Mac operating system, so please only use this if you have
a valid Microsoft account. If you do think you have the wits to get Microsoft authentication working on a fifteen-year-old
Mac operating system then please get in touch with me.