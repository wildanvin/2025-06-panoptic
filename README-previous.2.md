# Panoptic audit details
- Total Prize Pool: $18,000 in USDC
  - HM awards: up to $14,400 in USDC
    - If no valid Highs or Mediums are found, the HM pool is $0 
  - QA awards: $600 in USDC
  - Judge awards: $2,500 in USDC
  - Scout awards: $500 USDC
- [Read our guidelines for more details](https://docs.code4rena.com/competitions)
- Starts June 27, 2025 20:00 UTC
- Ends July 7, 2025 20:00 UTC

**❗ Important notes for wardens** 
1. A coded, runnable PoC is required for all High/Medium submissions to this audit. 
   - This repo includes a basic template to run the test suite.
   - PoCs must use the test suite provided in this repo.
   - Your submission will be marked as Insufficient if the POC is not runnable and working with the provided test suite.
   - Exception: PoC is optional (though recommended) for wardens with signal ≥ 0.68.
2. Judging phase risk adjustments (upgrades/downgrades):
   - High- or Medium-risk submissions downgraded by the judge to Low-risk (QA) will be ineligible for awards.
   - Upgrading a Low-risk finding from a QA report to a Medium- or High-risk finding is not supported.
   - As such, wardens are encouraged to select the appropriate risk level carefully during the submission phase.

## Automated Findings / Publicly Known Issues

The 4naly3er report can be found [here](https://github.com/code-423n4/YYYY-MM-contest-candidate/blob/main/4naly3er-report.md).

_Note for C4 wardens: Anything included in this `Automated Findings / Publicly Known Issues` section is considered a publicly known issue and is ineligible for awards._

Managers and owners have a great deal of influence over the operations of the vault contract and the accountant contract -- these roles should be considered trusted such that issues requiring malicious intent, "user error", or action from anything other than an untrusted user are not valid.

Performance fees may be under or over-charged.

Users may lose small amounts of funds due to rounding (in particular if their deposits/withdrawals are executed over many epochs) -- assume that 1 unit of underlying token always represents an inconsequential amount of value. 

It is assumed that the sum of the amount of underlying tokens in existence and the value of the vault does not exceed 2^126 - 1 at any point -- in general, issues requiring a large token supply or value as a prerequisite are not valid.


✅ SCOUTS: Please format the response above 👆 so its not a wall of text and its readable.

# Overview

[ ⭐️ SPONSORS: add info here ]

## Links

- **Previous audits:**  
  - ✅ SCOUTS: If there are multiple report links, please format them in a list.
- **Documentation:** https://panoptic.xyz/docs/intro
- **Website:** https://panoptic.xyz/
- **X/Twitter:** https://x.com/panoptic_xyz 

---

# Scope

[ ✅ SCOUTS: add scoping and technical details here ]

### Files in scope
- ✅ This should be completed using the `metrics.md` file
- ✅ Last row of the table should be Total: SLOC
- ✅ SCOUTS: Have the sponsor review and and confirm in text the details in the section titled "Scoping Q amp; A"

*For sponsors that don't use the scoping tool: list all files in scope in the table below (along with hyperlinks) -- and feel free to add notes to emphasize areas of focus.*

| Contract | SLOC | Purpose | Libraries used |  
| ----------- | ----------- | ----------- | ----------- |
| [contracts/folder/sample.sol](https://github.com/code-423n4/repo-name/blob/contracts/folder/sample.sol) | 123 | This contract does XYZ | [`@openzeppelin/*`](https://openzeppelin.com/contracts/) |

### Files out of scope
✅ SCOUTS: List files/directories out of scope

# Additional context

## Areas of concern (where to focus for bugs)
None

✅ SCOUTS: Please format the response above 👆 so its not a wall of text and its readable.

## Main invariants

Deposits and withdrawals made in the current epoch cannot be executed until the manager fulfills and advances the epoch
Only deposits/withdrawals in the current epoch can be cancelled
Only the manager can cancel or fulfill deposits/withdrawals
A user with a deposit/withdrawal active in a given epoch should not have more than amount*fulfilled/total (shares for withdrawals, assets for deposits) fulfilled in that epoch, although they may have funds in that epoch rolled over from previous epochs that won't be withdrawn until previous epochs are executed and the state is moved.
The fulfilled amount cannot exceed the deposited/withdrawn amount for a given epoch

✅ SCOUTS: Please format the response above 👆 so its not a wall of text and its readable.

## All trusted roles in the protocol

Hypovault Owner - controls accountant, fee wallet, and manager address
Hypovault Manager - handles deposit/withdrawal execution and can make arbitrary calls for vault management
Hypovault fee wallet - receives performance fee tokens
Accountant owner - updates pool list on the accountant contract 

✅ SCOUTS: Please format the response above 👆 using the template below👇

| Role                                | Description                       |
| --------------------------------------- | ---------------------------- |
| Owner                          | Has superpowers                |
| Administrator                             | Can change fees                       |

✅ SCOUTS: Please format the response above 👆 so its not a wall of text and its readable.

## Running tests

git clone https://github.com/panoptic-labs/hypovault --recurse-submodules
cd hypovault
foundryup
forge build
forge test

✅ SCOUTS: Please format the response above 👆 using the template below👇

```bash
git clone https://github.com/code-423n4/2023-08-arbitrum
git submodule update --init --recursive
cd governance
foundryup
make install
make build
make sc-election-test
```
To run code coverage
```bash
make coverage
```

✅ SCOUTS: Add a screenshot of your terminal showing the test coverage

## Miscellaneous
Employees of Panoptic and employees' family members are ineligible to participate in this audit.

Code4rena's rules cannot be overridden by the contents of this README. In case of doubt, please check with C4 staff.



# Scope

*See [scope.txt](https://github.com/code-423n4/2025-06-panoptic/blob/main/scope.txt)*

### Files in scope


| File   | Logic Contracts | Interfaces | nSLOC | Purpose | Libraries used |
| ------ | --------------- | ---------- | ----- | -----   | ------------ |
| /src/HypoVault.sol | 1| **** | 272 | |lib/panoptic-v1.1/contracts/tokens/ERC20Minimal.sol<br>lib/panoptic-v1.1/lib/openzeppelin-contracts/contracts/token/ERC20/IERC20.sol<br>lib/panoptic-v1.1/contracts/base/Multicall.sol<br>lib/panoptic-v1.1/lib/openzeppelin-contracts/contracts/access/Ownable.sol<br>lib/panoptic-v1.1/lib/openzeppelin-contracts/contracts/utils/Address.sol<br>lib/panoptic-v1.1/contracts/libraries/Math.sol<br>lib/panoptic-v1.1/contracts/libraries/SafeTransferLib.sol|
| /src/accountants/PanopticVaultAccountant.sol | 1| **** | 171 | |lib/panoptic-v1.1/lib/openzeppelin-contracts/contracts/access/Ownable.sol<br>lib/panoptic-v1.1/contracts/libraries/Math.sol<br>lib/panoptic-v1.1/contracts/libraries/PanopticMath.sol<br>lib/panoptic-v1.1/contracts/tokens/interfaces/IERC20Partial.sol<br>lib/panoptic-v1.1/contracts/interfaces/IV3CompatibleOracle.sol<br>lib/panoptic-v1.1/contracts/PanopticPool.sol<br>lib/panoptic-v1.1/contracts/types/LeftRight.sol<br>lib/panoptic-v1.1/contracts/types/LiquidityChunk.sol<br>lib/panoptic-v1.1/contracts/types/PositionBalance.sol<br>lib/panoptic-v1.1/contracts/types/TokenId.sol|
| **Totals** | **2** | **** | **443** | | |

### Files out of scope

*See [out_of_scope.txt](https://github.com/code-423n4/2025-06-panoptic/blob/main/out_of_scope.txt)*

| File         |
| ------------ |
| ./src/interfaces/IVaultAccountant.sol |
| ./test/HypoVault.t.sol |
| ./test/PanopticVaultAccountant.t.sol |
| Totals: 3 |

