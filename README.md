Algorithm optimization experiments of state-of-the-art EVM fuzzer Ityfuzz [\[Link\]](https://docs.ityfuzz.rs)

## Steps to Build:
1. Checkout branch `gmq_edg_exp`
2. Navigate to cargo root
```bash
cd .${Your Work Directory}/fuzzOn
```
3. Scheduler Experiments:
   1. Build project with `use_favored` flag enabled
      ```bash
      cargo build --features "cmp dataflow evm print_txn_corpus full_trace force_cache use_favored" --no-default-features
      ```
   2. Run projects from CLI
      1. Favored function sequence + favored function signatures
         1. AES
             ```bash
             ./target/release/ityfuzz evm -t 0x55d398326f99059fF775485246999027B3197955,0x40eD17221b3B2D8455F4F1a05CAc6b77c5f707e3,0xdDc0CFF76bcC0ee14c3e73aF630C029fe020F907 -c bsc --onchain-block-number 23695904 -f --onchain-etherscan-api-key HZF74EH51PK2W1N84BE6W8YYATDP6UEFC2 --favored-file-path ./tests/presets/favored_sigs_aes.json
             ```
         2. BGLD
            ```bash
            ./target/release/ityfuzz evm -t 0x55d398326f99059fF775485246999027B3197955,0xE445654F3797c5Ee36406dBe88FBAA0DfbdDB2Bb,0x429339fa7A2f2979657B25ed49D64d4b98a2050d,0xbb4CdB9CBd36B01bD1cBaEBF2De08d9173bc095c,0xC2319E87280c64e2557a51Cb324713Dd8d1410a3,0x169f715CaE1F94C203366a6890053E817C767B7C,0x559D0deAcAD259d970f65bE611f93fCCD1C44261,0x7526cC9121Ba716CeC288AF155D110587e55Df8b,0x0fe261aeE0d1C4DFdDee4102E82Dd425999065F4,0xC632F90affeC7121120275610BF17Df9963F181c -c bsc --onchain-block-number 23844529 -f --onchain-etherscan-api-key QY1M8Y2SX1J2MGY58H54IVRV9MEII1MT5D --favored-file-path ./tests/presets/favored_sigs_bgld.json
            ```
         3. NOVO
            ```bash
            ./target/release/ityfuzz evm -t 0xEeBc161437FA948AAb99383142564160c92D2974,0xa0787daad6062349f63b7c228cbfd5d8a3db08f1,0x3463a663de4ccc59c8b21190f81027096f18cf2a,0x6Fb2020C236BBD5a7DDEb07E14c9298642253333,0xbb4CdB9CBd36B01bD1cBaEBF2De08d9173bc095c,0x128cd0Ae1a0aE7e67419111714155E1B1c6B2D8D -c bsc --onchain-block-number 18225002 -f --onchain-etherscan-api-key HZF74EH51PK2W1N84BE6W8YYATDP6UEFC2 --favored-file-path ./tests/presets/favored_sigs_novo.json
            ```
         4. YYDS
            ```bash
            ./target/release/ityfuzz evm -t 0x55d398326f99059fF775485246999027B3197955,0x970A76aEa6a0D531096b566340C0de9B027dd39D,0xB19463ad610ea472a886d77a8ca4b983E4fAf245,0xd5cA448b06F8eb5acC6921502e33912FA3D63b12,0xbb4CdB9CBd36B01bD1cBaEBF2De08d9173bc095c,0xe70cdd37667cdDF52CabF3EdabE377C58FaE99e9 -c bsc --onchain-block-number 21157025 -f --onchain-etherscan-api-key HZF74EH51PK2W1N84BE6W8YYATDP6UEFC2 --favored-file-path ./tests/presets/favored_sigs_yyds.json
            ```
      2. Favored function signatures only: remove the `calls` field from `./tests/presets/favored_sigs_{project}.json`
   3. Run projects from IDE
      1. Favored function sequence + favored function signatures
         1. AES
            ```
            run  --features "cmp dataflow evm print_txn_corpus full_trace force_cache use_favored" --no-default-features  --  evm -t 0x55d398326f99059fF775485246999027B3197955,0x40eD17221b3B2D8455F4F1a05CAc6b77c5f707e3,0xdDc0CFF76bcC0ee14c3e73aF630C029fe020F907 -c bsc --onchain-block-number 23695904 -f --onchain-etherscan-api-key HZF74EH51PK2W1N84BE6W8YYATDP6UEFC2 --favored-file-path ./tests/presets/favored_sigs_aes.json
            ```
         2. BGLD
            ```
            run  --features "cmp dataflow evm print_txn_corpus full_trace force_cache use_favored" --no-default-features  --  evm -t 0x55d398326f99059fF775485246999027B3197955,0xE445654F3797c5Ee36406dBe88FBAA0DfbdDB2Bb,0x429339fa7A2f2979657B25ed49D64d4b98a2050d,0xbb4CdB9CBd36B01bD1cBaEBF2De08d9173bc095c,0xC2319E87280c64e2557a51Cb324713Dd8d1410a3,0x169f715CaE1F94C203366a6890053E817C767B7C,0x559D0deAcAD259d970f65bE611f93fCCD1C44261,0x7526cC9121Ba716CeC288AF155D110587e55Df8b,0x0fe261aeE0d1C4DFdDee4102E82Dd425999065F4,0xC632F90affeC7121120275610BF17Df9963F181c -c bsc --onchain-block-number 23844529 -f --onchain-etherscan-api-key QY1M8Y2SX1J2MGY58H54IVRV9MEII1MT5D --favored-file-path ./tests/presets/favored_sigs_bgld.json
            ```
         3. NOVO
            ```
            run  --features "cmp dataflow evm print_txn_corpus full_trace force_cache use_favored" --no-default-features  -- evm -t 0xEeBc161437FA948AAb99383142564160c92D2974,0xa0787daad6062349f63b7c228cbfd5d8a3db08f1,0x3463a663de4ccc59c8b21190f81027096f18cf2a,0x6Fb2020C236BBD5a7DDEb07E14c9298642253333,0xbb4CdB9CBd36B01bD1cBaEBF2De08d9173bc095c,0x128cd0Ae1a0aE7e67419111714155E1B1c6B2D8D -c bsc --onchain-block-number 18225002 -f --onchain-etherscan-api-key HZF74EH51PK2W1N84BE6W8YYATDP6UEFC2 --favored-file-path ./tests/presets/favored_sigs_novo.json
            ```
         4. YYDS
            ```
            run  --features "cmp dataflow evm print_txn_corpus full_trace force_cache use_favored" --no-default-features  -- evm -t 0x55d398326f99059fF775485246999027B3197955,0x970A76aEa6a0D531096b566340C0de9B027dd39D,0xB19463ad610ea472a886d77a8ca4b983E4fAf245,0xd5cA448b06F8eb5acC6921502e33912FA3D63b12,0xbb4CdB9CBd36B01bD1cBaEBF2De08d9173bc095c,0xe70cdd37667cdDF52CabF3EdabE377C58FaE99e9 -c bsc --onchain-block-number 21157025 -f --onchain-etherscan-api-key HZF74EH51PK2W1N84BE6W8YYATDP6UEFC2 --favored-file-path ./tests/presets/favored_sigs_yyds.json
            ```
      2. Favored function signatures only: remove the `calls` field from `./tests/presets/favored_sigs_{project}.json`
4. Mutator Experiments:

## Performance