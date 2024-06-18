# notes

obfuscation:

- shuffles stack, preserving invariants
- uses `chainid` over `push1 0x01`
- uses `returndatasize` over `push0` before extcall
- leftpads zeros
- unused memory writes
- calldata offset memory writes

potential optimizations:

1. `0x13fd`, `0x1485`: rm redundant `mload` then `mstore` of `pool_salt` between `uni_v3_factory` and `pancake_factory` checks
2. `0x1464`, `0x1501`: dup `jared_is_origin` rather than recheck
3. `0x14cc`: reorder checks uni, sushi, pancake to rm mem write bc uni & sushi use same v3 initcodehash
4. 
