//Duckcoin ico

//Compiler version number
pragma solidity ^0.4.11;

contract solidity{
    
    //Introducing the maximum number of duckcoins available for sale
    uint public max_duckcoins = 1000000;
    
    //Intrducing the dollar to duckcoin conversion rate
    uint public usd_to_duckcoin = 1000;
    
    //Introducing the total number of duckcoins bought
    uint public total_duckcoin_bought = 0;
    
    //Mapping from the ib=nvestor address to its equity in  duckcoin and usd
    mapping(address => unit) equity_duckcoin;
    mapping(address => unit) equity_usd;
    
    //Check if an investor can buy Hadcoin
    modifier can_buy_duckcoin(uint usd_invested){
        require(usd_invested * usd_to_duckcoin + total_duckcoin_bought <= max_duckcoins);
    _;
    }
    
    //Getting the equity in duckcoin of an investor
    function equity_in_duckcoin(address investor) external constant returns(uint){
        return equity_duckcoin(investor);
    }
    
    //Getting the equity in usd of an investor
    function equity_in_usd(address investor) external constant returns(uint){
        return equity_usd(investor);
    }
    
    //Buy duckcoins
    function buy_duckcoins(address investor, uint usd_invested) external
    can_buy_duckcoin(usd_invested){
        had_bought_duckcoin = usd_invested * usd_to_duckcoin;
        equity_duckcoin += had_bought_duckcoin;
        equity_usd += usd_invested;
        total_duckcoin_bought += had_bought_duckcoin;
    }
    
    //Selling duckcoins
    function sell_duckcoins(address investor, uint duckcoins_sold) external {
        equity_duckcoin -= duckcoins_sold;
        equity_usd -= duckcoins_sold/1000;
        total_duckcoin_bought -= duckcoins_sold;
    }
    
}