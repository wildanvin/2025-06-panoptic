

# Scope

*See [scope.txt](https://github.com/code-423n4/2025-06-panoptic/blob/main/scope.txt)*

### Files in scope


| File   | Logic Contracts | Interfaces | nSLOC | Purpose | Libraries used |
| ------ | --------------- | ---------- | ----- | -----   | ------------ |
| /src/HypoVault.sol | 1| **** | 272 | |lib/panoptic-v1.1/contracts/tokens/ERC20Minimal.sol<br>lib/panoptic-v1.1/lib/openzeppelin-contracts/contracts/token/ERC20/IERC20.sol<br>lib/panoptic-v1.1/contracts/base/Multicall.sol<br>lib/panoptic-v1.1/lib/openzeppelin-contracts/contracts/access/Ownable.sol<br>lib/panoptic-v1.1/lib/openzeppelin-contracts/contracts/utils/Address.sol<br>lib/panoptic-v1.1/contracts/libraries/Math.sol<br>lib/panoptic-v1.1/contracts/libraries/SafeTransferLib.sol|
| /src/accountants/PanopticVaultAccountant.sol | 1| **** | 172 | |lib/panoptic-v1.1/lib/openzeppelin-contracts/contracts/access/Ownable.sol<br>lib/panoptic-v1.1/contracts/libraries/Math.sol<br>lib/panoptic-v1.1/contracts/libraries/PanopticMath.sol<br>lib/panoptic-v1.1/contracts/tokens/interfaces/IERC20Partial.sol<br>lib/panoptic-v1.1/contracts/interfaces/IV3CompatibleOracle.sol<br>lib/panoptic-v1.1/contracts/PanopticPool.sol<br>lib/panoptic-v1.1/contracts/types/LeftRight.sol<br>lib/panoptic-v1.1/contracts/types/LiquidityChunk.sol<br>lib/panoptic-v1.1/contracts/types/PositionBalance.sol<br>lib/panoptic-v1.1/contracts/types/TokenId.sol|
| **Totals** | **2** | **** | **444** | | |

### Files out of scope

*See [out_of_scope.txt](https://github.com/code-423n4/2025-06-panoptic/blob/main/out_of_scope.txt)*

| File         |
| ------------ |
| ./src/interfaces/IVaultAccountant.sol |
| ./test/HypoVault.t.sol |
| ./test/PanopticVaultAccountant.t.sol |
| Totals: 3 |

