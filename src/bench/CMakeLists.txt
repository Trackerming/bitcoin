project(bitcoin-bench)

add_executable(bitcoin-bench
        EXCLUDE_FROM_ALL
        base58.cpp
        bench.cpp
        bench_bitcoin.cpp
        #cashaddr.cpp
        block_assemble.cpp
        ccoins_caching.cpp
        chacha20.cpp
        checkblock.cpp

        #	checkblock.cpp TODO Fix including bench/data/*.raw files
        checkqueue.cpp
        coin_selection.cpp
        crypto_hash.cpp
        duplicate_inputs.cpp
        Examples.cpp
        gcs_filter.cpp
        lockedpool.cpp
        mempool_eviction.cpp
        merkle_root.cpp
        poly1305.cpp
        #perf.cpp
        prevector.cpp
        rollingbloom.cpp
        rpc_mempool.cpp
        util_time.cpp
        verify_script.cpp
        wallet_balance.cpp
        )

target_link_libraries(bitcoin-bench common bitcoinconsensus server)

if(BUILD_BITCOIN_WALLET)
    target_sources(bitcoin-bench PRIVATE coin_selection.cpp)
endif()

add_custom_target(bench-bitcoin
        COMMAND
        ./bitcoin-bench
        DEPENDS
        bitcoin-bench
        )