

function checkCashRegister(price, cash, cid) {
  var result;
  var coinsValues = [[0.01,0], [0.05,0], [0.1,0], [0.25,0], [1,0], [5,0], [10,0], [20,0], [100,0]];
  result = {status:0, change:0}
  // Here is your change, ma'am.
  if (price > cash) {
    change.status = "INSUFFICIENT_FUNDS";
    change.result = [];
    return result
  } 

  var sumInHand = sumInHand(cid);

  var coinsList = changeAvailable(cid, coinsValues);
  // console.log(coinsList);

  var changeToGive = cash - price;
  // console.log(changeToGive);

  var changeGivenAndRusltMessage = coinsToGive(changeToGive, coinsList);

  var changeGiven = changeGivenAndRusltMessage[0];
  // console.log(changeGiven);

  var resultDone = changeBack(cid, changeGiven, coinsValues);
  result.change = resultDone;

  var reusltMessage = changeGivenAndRusltMessage[1];
  result.status = reusltMessage;

  if (reusltMessage == "OPEN" && changeToGive - sumInHand == 0) {
    result.status = "CLOSED";
    var cidCopy = cid;
    for (let i in cidCopy) {
      for (let j in resultDone) {
        if (cidCopy[i][0] == resultDone[j][0]) {
          cidCopy[i][1] = resultDone[j][1];
        }
      }
    }
    result.change = cidCopy;
  }

  function coinsToGive(changeToHandOut, coinsInHand) {
    var allCoinResult = [];
    var changeDone = false;
    changeToHandOut = Number(changeToHandOut).toFixed(2);
    for (let j in coinsInHand) {
      var currentCoin = coinsInHand[coinsInHand.length - j - 1];
      var currentCoinFace = Number(currentCoin[0]).toFixed(2);
      var currentCoinSum = Number(currentCoin[1]).toFixed(2);
      // console.log("currentCoin", currentCoinFace, currentCoinSum, changeToHandOut)

      if (Number(currentCoinFace) <= Number(changeToHandOut)) {
        // console.log("aaa", currentCoinFace, changeToHandOut);
        // console.log(currentCoin);
        var coinBefore = currentCoinSum;
        while (Number(currentCoinFace) <= Number(changeToHandOut) && Number(currentCoinFace) <= Number(currentCoinSum)) {
          // console.log("while run, changeToHandOut", changeToHandOut, currentCoinSum);
          changeToHandOut = changeToHandOut - currentCoinFace;
          currentCoinSum = currentCoinSum - currentCoinFace;
          changeToHandOut = Number(changeToHandOut).toFixed(2);
          currentCoinSum = Number(currentCoinSum).toFixed(2);
          // console.log(currentCoin)
        }
        var coinResult = [currentCoinFace, Number(coinBefore - currentCoinSum).toFixed(2)];
        changeToHandOut = Number(changeToHandOut).toFixed(2);
        // console.log(coinResult + " changeToHandOut " + changeToHandOut);
        allCoinResult.push(coinResult);

        if (changeToHandOut == 0) {
          changeDone = true;
        }
      }
      // console.log("--------------- NEXT COIN ---------------");
    }

    var statusMessage = "OPEN";
    if (!(changeDone)) {
      statusMessage = "INSUFFICIENT_FUNDS";
      allCoinResult = [];
    }
    return [allCoinResult, statusMessage];
  }

  function changeAvailable(coins, coinsValues) {
    // var coinsValues = [[0.01,0], [0.05,0], [0.1,0], [0.25,0], [1,0], [5,0], [10,0], [20,0], [100,0]];
    for (let i in coinsValues) {
      coinsValues[i][1] = coins[i][1]
    }
    return coinsValues
  }

  function changeBack(coins, result, coinsValues) {
    // var coinsValues = [[0.01,0], [0.05,0], [0.1,0], [0.25,0], [1,0], [5,0], [10,0], [20,0], [100,0]];
    for (let i in coinsValues) {
      coinsValues[i][1] = coins[i][0]
    }
    // console.log(coinsValues)
    for (let j in result) {
      for (let k in coinsValues) {
        if (result[j][0] == coinsValues[k][0]) {
          result[j][0] = coinsValues[k][1];
          result[j][1] = Number(result[j][1]);
        }
      }
    }
    return result;
  }

  function sumInHand(cid) {
    var sum = 0;
    for (let i in cid) {
      sum += Number(cid[i][1]);
    }
    sum = sum.toFixed(2);
    sum = Number(sum);
    return sum;
  }

  console.log(result);
  console.log("--------------- NEXT CHECK ---------------");
  return result;
}

// Example cash-in-drawer array:
// [["PENNY", 1.01],
// ["NICKEL", 2.05],
// ["DIME", 3.1],
// ["QUARTER", 4.25],
// ["ONE", 90],
// ["FIVE", 55],
// ["TEN", 20],
// ["TWENTY", 60],
// ["ONE HUNDRED", 100]]

checkCashRegister(19.5, 20, [["PENNY", 1.01], ["NICKEL", 2.05], ["DIME", 3.1], ["QUARTER", 4.25], ["ONE", 90], ["FIVE", 55], ["TEN", 20], ["TWENTY", 60], ["ONE HUNDRED", 100]]);
checkCashRegister(3.26, 100, [["PENNY", 1.01], ["NICKEL", 2.05], ["DIME", 3.1], ["QUARTER", 4.25], ["ONE", 90], ["FIVE", 55], ["TEN", 20], ["TWENTY", 60], ["ONE HUNDRED", 100]]);
checkCashRegister(19.5, 20, [["PENNY", 0.01], ["NICKEL", 0], ["DIME", 0], ["QUARTER", 0], ["ONE", 0], ["FIVE", 0], ["TEN", 0], ["TWENTY", 0], ["ONE HUNDRED", 0]])
checkCashRegister(19.5, 20, [["PENNY", 0.01], ["NICKEL", 0], ["DIME", 0], ["QUARTER", 0], ["ONE", 1], ["FIVE", 0], ["TEN", 0], ["TWENTY", 0], ["ONE HUNDRED", 0]])
checkCashRegister(19.5, 20, [["PENNY", 0.5], ["NICKEL", 0], ["DIME", 0], ["QUARTER", 0], ["ONE", 0], ["FIVE", 0], ["TEN", 0], ["TWENTY", 0], ["ONE HUNDRED", 0]])



