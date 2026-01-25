
cmake_minimum_required(VERSION 3.4.1)

project(netblock)

add_library( netblock
             SHARED
             src/main/jni/netblock/netblock.c
             src/main/jni/netblock/session.c
             src/main/jni/netblock/ip.c
             src/main/jni/netblock/tcp.c
             src/main/jni/netblock/udp.c
             src/main/jni/netblock/icmp.c
             src/main/jni/netblock/tls.c
             src/main/jni/netblock/dns.c
             src/main/jni/netblock/dhcp.c
             src/main/jni/netblock/pcap.c
             src/main/jni/netblock/util.c )

include_directories( src/main/jni/netblock/ )

find_library( log-lib
              log )

target_link_libraries( netblock
                       ${log-lib} )

target_link_options(netblock PRIVATE "-Wl,-z,max-page-size=16384")
