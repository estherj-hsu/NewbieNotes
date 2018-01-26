## Scope
 - function 內以 `var` 宣告變數，此變數僅能在 function 中使用。
 - function 內未以 `var` 宣告變數，且同時有同名廣域變數存在時，function 內變數會被視為廣域變數。
 - 在區域中以 `var` 宣告變數，但未初始化（給予值），該變數可被存取但無定義。

## Naming
 - 私有變數以 `_` 為前綴
 - 類別物件大寫字母開始、函式與變數以小寫字母開始
 - 函式名稱為動詞、變數名稱為名詞
 - 變數 `let`：可隨時改變的值、**小駝峰式**命名
 - 常數 `let`：可隨時改變的值、**大寫**命名


## `groupBy` & `sumBy`

### Goal

get data and group by specific key, then create a new object
use lodash `_.groupBy` & `_.sumBy`

#### Original data

    [
      {
        "id": 1,
        "name": "Esther",
        "saving": {
          "currency": "USD",
          "amount": 100
        }
      },
      {
        "id": 2,
        "name": "Alice",
        "saving": {
          "currency": "TWD",
          "amount": 100
        }
      },
      {
        "id": 3,
        "name": "Tim",
        "saving": {
          "currency": "USD",
          "amount": 500
        }
      }
    ]

#### Grouped Data

    [
	    {
		    "currency": "USD",
		    "amount": 600
	    },
	    {
		    "currency": "TWD",
		    "amount": 100
	    },

    ]


### Solutions

#### Solution 1

	function getSavingByCurrency(savingData) {
	  const groupData = _.groupBy(
	    savingData,
	    (data) => data.saving.currency
	  );
	  const res = Object.entries(groupData)
	    .map(([currency, users]) => ({
	      currency: currency,
	      amount: _.sumBy(users, (user) => user.saving.amount),
	    }));
	  return res;
	}

#### Solution 2

	function getSavingByCurrency(savingData) {
	  const res = Object.entries(_.groupBy(savingData, 'saving.currency'))
	    .map(([currency, users]) => ({
	      currency: currency,
	      amount: _.sumBy(users, 'saving.amount') }),
	    );
	  return res;
	}
