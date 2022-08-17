Additional jars you'll need to download:
- https://repo1.maven.org/maven2/com/google/guava/guava-jdk5/17.0/guava-jdk5-17.0.jar
- https://repo.maven.apache.org/maven2/org/apache/sanselan/sanselan/0.97-incubator/sanselan-0.97-incubator.jar
- https://libraries.minecraft.net/net/java/jutils/jutils/1.0.0/jutils-1.0.0.jar
- https://libraries.minecraft.net/com/paulscode/soundsystem/20120107/soundsystem-20120107.jar
- https://libraries.minecraft.net/com/google/code/gson/gson/2.2.4/gson-2.2.4.jar
- https://libraries.minecraft.net/com/paulscode/librarylwjglopenal/20100824/librarylwjglopenal-20100824.jar
- https://libraries.minecraft.net/com/ibm/icu/icu4j-core-mojang/51.2/icu4j-core-mojang-51.2.jar
- https://libraries.minecraft.net/net/sf/jopt-simple/jopt-simple/4.6/jopt-simple-4.6.jar
- https://repo1.maven.org/maven2/org/slf4j/slf4j-api/1.7.21/slf4j-api-1.7.21.jar
- https://repo1.maven.org/maven2/org/slf4j/slf4j-simple/1.7.21/slf4j-simple-1.7.21.jar
- https://archive.apache.org/dist/commons/codec/binaries/commons-codec-1.6-bin.zip (extract)
- https://archive.apache.org/dist/commons/io/binaries/commons-io-2.2-bin.zip (extract)
- https://archive.apache.org/dist/commons/lang/binaries/commons-lang3-3.1-bin.zip (extract)

Jars you'll need to compile:
- https://github.com/Camotoy/codecjorbis

Explaining jars here:
- Fastutil is compiled in Java 5 and commenting out some classes that don't exist in Java 5
- The Netty classes here I built when working on porting 1.7. They are cursed and I really don't nk the world need to see source code for it.
- The Log4J jars are the last Java 6-supported Log4j2 versions backported to Java 5. 
- The LWJGL jars are here because while I have the source available (https://github.com/Camotoy/lwjgl/tree/powerpchack) it's a pain to compile - I believe I needed to use a Snow Leopard computer