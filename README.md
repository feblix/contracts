# Feblix (FBLX) Contracts

### Contract Address: 0xcd7b102d82b9a8f089669d2afa74ad2a121ac137
### White Paper: [Feblix Whitepaper](https://feblix.finance/white-paper.pdf)

## Smart Contract
### BEP-20
Feblix is an BEP-20 contract that implements the following interface:
```Solidity
interface IERC20 {
    function totalSupply() external view returns (uint256);
    function balanceOf(address account) external view returns (uint256);
    function transfer(address recipient, uint256 amount) external returns (bool);
    function allowance(address owner, address spender) external view returns (uint256);
    function approve(address spender, uint256 amount) external returns (bool);
    function transferFrom(address sender, address recipient, uint256 amount) external returns (bool);
    event Transfer(address indexed from, address indexed to, uint256 value);
    event Approval(address indexed owner, address indexed spender, uint256 value);
}
```

### UniSwap Factory and Exchange
Feblix uses the PancakeSwap contracts to enable swapping tokens:

```Solidity
// PancakeSwap Interface
interface IFactory{
        function createPair(address tokenA, address tokenB) external returns (address pair);
        function getPair(address tokenA, address tokenB) external view returns (address pair);
}
```

### Feblix Public Get Methods
The following public getters are available to query:
```Solidity
// Public Parameters
address payable public marketingWallet = payable(0xcb7af6e92479f93a49013f19600444dc440a41ab);
address payable public rewardsWallet = payable(0x591f2da99e9f7658a76e70b03e899ab74f624f19);
address public deadAddress = address(0x000000000000000000000000000000000000dEaD); 
address private deployerAddress = address(0x0000000000000000000000000000000000000000); 
IRouter public pancakeRouter;
address public pancakePair;
bool internal inSwap;
bool public swapEnabled = true;
uint256 private minTokensToSwap = _tTotal/1000;
uint256 public maxTxAmount = _tTotal/200;
uint256 public maxWalletTokens = _tTotal/100;

// Public Get Functions
function name() public view returns (string memory)
function symbol() public view returns (string memory)
function decimals() public view returns (uint8)
function totalSupply() public view override returns (uint256)
function balanceOf(address account) public view override returns (uint256)
function transfer(address recipient, uint256 amount) public override returns (bool)
function allowance(address owner, address spender) public view override returns (uint256)
function approve(address spender, uint256 amount) public override returns (bool)
function transferFrom(address sender, address recipient, uint256 amount) public override returns (bool)
function increaseAllowance(address spender, uint256 addedValue) public virtual returns (bool)
function decreaseAllowance(address spender, uint256 subtractedValue) public virtual returns (bool)
function isExcludedFromReward(address account) public view returns (bool)
function totalFeesCharged() public view returns (uint256)
```

### Feblix Public Transactions
The following public transaction functions are available to call:
```Solidity
receive() external payable
function isExcludedFromFee(address account) public view returns(bool)
function burn(uint256 amount) external
function transfer(address recipient, uint256 amount) public override returns (bool)
function approve(address spender, uint256 amount) public override returns (bool) 
function transferFrom(address sender, address recipient, uint256 amount) public override returns (bool)
function deliver(uint256 tAmount) public
```

### Constructor
There are three constructor options:

**Mainnet**

This is the constructor deployed to mainnet:

```Solidity
//mainnet
_name = "FEBLIX"; _symbol = "FBLX"; _decimals = 9;
MAX = ~uint256(0); _tTotal = 100000000000 * 10**6 * 10**9; _rTotal = (MAX - (MAX % _tTotal));
burnAddress = 0x000000000000000000000000000000000000dEaD;
address payable public marketingWallet = payable(0xcb7af6e92479f93a49013f19600444dc440a41ab);
address payable public rewardsWallet = payable(0x591f2da99e9f7658a76e70b03e899ab74f624f19);
IRouter _pancakeRouter = IRouter(0x10ED43C718714eb63d5aA57B78B54704E256024E);

```
