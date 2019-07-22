project(wallet)

# Add Berkeley DB dependency.
#find_package(BerkeleyDB REQUIRED)

# Add event dependency. This is only required for evhttp_uridecode
# in rpcwallet.cpp so it may be worth considering using an alternative.
#find_package(Event REQUIRED)

add_library(wallet
        ../interfaces/wallet.cpp
        coincontrol.cpp
        coinselection.cpp
        crypter.cpp
        db.cpp
        fees.cpp
        feebumper.cpp
        #finaltx.cpp
        init.cpp
        load.cpp
        psbtwallet.cpp
        rpcdump.cpp
        rpcwallet.cpp
        wallet.cpp
        walletdb.cpp
        wallettool.cpp
        walletutil.cpp
        )

target_link_libraries(wallet common univalue Event ${BDBXX_LIBRARY})

target_include_directories(wallet PUBLIC ${BDBXX_INCLUDE_DIR})
