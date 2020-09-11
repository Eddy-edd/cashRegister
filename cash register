const REGISTER_STATUS={
    closed: 'CLOSED',
    insufficientFunds:'INSUFFICIENT_FUNDS',
    open:'OPEN'
} 

function checkCashRegister(price,cash,cid){
    let cashRegister = { status: '', change: cid};
    const changeRequired= parseFloat(cash - price).toFixed(2);
    const changeAvailable = getTotalCashRegisterChange(cid);
    cashRegister.status = getTotalCashRegisterStatus(changeRequired, changeAvailable);

    

if(cashRegister.status === REGISTER_STATUS.insufficientFunds){
    cashRegister.change = [];

    return cashRegister;
}

cashRegister.change = getCustomersChange(changeRequired, cid);
console.log(changeRequired);
console.log(cashRegister);
if (changeRequired > getTotalCashRegisterStatus(cashRegister.change)){
    console.log(changeRequired)
    cashRegister.status = REGISTER_STATUS.insufficientFunds;
    cashRegister.change = [];
}

if(cashRegister.status === REGISTER_STATUS.closed){
    cashRegister.change = [...cid]
}

return cashRegister;

}

function getCustomersChange(changeRequired,cid){
    const change =[];
    const currencyDictionary ={
        "PENNY":0.01,
        "NICKEL":0.05,
        "Dime":0.10,
        "QUARTER":0.25,
        "ONE":1.0,
        "FIVE":5.00,
        "TEN":10.00,
        "TWENTY":20.00,
        "ONE HUNDRED":100.00
    };
    for (let i = cid.length - 1; i >= 0; i--){
        const currencyName = cid[i][0];
        const currencyTotal = cid[i][1];
        const currencyValue = currencyDictionary[currencyName];
        let currencyAmount = (currencyTotal/currencyValue).toFixed(2);
        let currencyToReturn = 0;
        
        while (changeRequired >= currencyValue && currencyAmount > 0 ){
            changeRequired -= currencyValue;
            changeRequired = changeRequired.toFixed(2);
            currencyAmount--;
            currencyToReturn++;
        }

        if(currencyToReturn > 0){
            change.push([currencyName, currencyToReturn * currencyValue]);
        }
    }
return change;
}
function getTotalCashRegisterStatus (changeRequired, changeAvailable){
    if(Number(changeRequired) > Number(changeAvailable)){
        return REGISTER_STATUS.insufficientFunds;
    }
    if(Number(changeRequired) < Number(changeAvailable)){
        return REGISTER_STATUS.open;
    }
    return REGISTER_STATUS.closed;

}
function getTotalCashRegisterChange(cid){
    let total = 0;
    for(let change of cid){
        let changeValue = change[1];
        total += changeValue;

    }
    return total.toFixed(2);
} 
console.log(checkCashRegister(19.5, 20, [["PENNY", 0.01], ["NICKEL", 0], ["DIME", 0], ["QUARTER", 0], ["ONE", 1], ["FIVE", 0], ["TEN", 0], ["TWENTY", 0], ["ONE HUNDRED", 0]]));
