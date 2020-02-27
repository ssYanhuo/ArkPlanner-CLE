# ArkPlanner API

> Request URL: [https://planner.penguin-stats.io/plan](https://planner.penguin-stats.io/)
>
> Request Method: ```POST```

## Post Parameters

- ```owned```: *dict*({item_name(*str*): count(*int*)})

*default: {}*

A dict of items owned, where keys are item names, i.e. 'D32钢', values are numbers of items owned.
-  ```required```: *dict*({item_name(*str*): count(*int*)}) 

*default: {}*

A dict of items required, where keys are item names, i.e. 'D32钢', values are numbers of items required.
- ```extra_outc```: *boolean*

*default: False*

Whether extra outcome of convertion is considered.
- ```convertion_dr```: *float* **NEW**

*default: 0.18*

The drop rate of extra outcome.
- ```exp_demand```: *boolean*

*default: True*

Whether Battle Record (作战记录) is considered valuable. If True, requirement of Battle Record is set to ```1e9```.
- ```gold_demand```: *boolean*

*default: True*

Whether LMD (龙门币) is considered valuable. If True, requirement of LMD is set to ```1e9```. If False, the value of Pure Gold is also considered 0.
- ```exclude```: list(str)  **NEW**

 *default: []*
 
Stages banned during calculation. Example: ```['1-7', 'SA-5']```
- ```store```: *boolean*  **NEW**

*default: True*

Whether to response green and yellow ticket values in stores.
## Response Parameters
- ```cost``` : *int*

Expected sanity cost. 
- ```gcost``` : *int*

Expected gold cost in convertion.
- ```gold``` : *int*

Expected gold gain in farming.
- ```exp``` : *int*

Expected exp gain in farming. Pure Gold not included.
- ```stages```: *list(stage*)

 ```
stage = {
	'stage': str, # stage name, eg. '1-7'
	'count': int, # times to farm
	'items': dict{str: int} # item_name: item_count
} 
 ```
 
Stages recommended to farm.
- ```syntheses```: *list(synthesis)*

 ```
synthesis= {
	'target': str, # target item name
	'count': int, # times to convert
	'materials': dict{str: int} # converted_item_name: item_count
} 
```

Convertions recommended.
- ```values```: *dict* {level *(str)*: value *(dict)* }

```
value = {
	'name': str, # item name
	'value': float # item value
}
```

Item values.
- ```green```: *dict* {item *(str)*: value *(float)* }  **NEW**
- ```yellow```: *dict* {item *(str)*: value *(float)* }  **NEW**

Value of one piece of green/yellow ticket when buying target items in the store.