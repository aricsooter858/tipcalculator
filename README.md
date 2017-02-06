# Tip Calculator

This program calculates initial cost, and then adds in state tax and a tip percentage to determine a final bill.

Websites used
* https://taxfoundation.org/state-and-local-sales-tax-rates-2016/

### Controller Code

```
myModule.controller('CostController',
        
            function ($scope) {
                    
                    var cc = this;
                    cc.cost = 0;
                    cc.subtotal = 0;
                    cc.tip = 0;
                    cc.total = 0;
                    
                    cc.updatetax = function updatetax(){
                        cc.subtotal = parseFloat(cc.cost) * cc.statetax.amount;
                        return cc.subtotal;
                        
                    }
                        
                    cc.updatetip = function updatetip(){
                        cc.tip = (parseFloat(cc.cost) * cc.tax) * cc.tippercent.amount;
                    }
                        

                    function update(){
                        cc.total = parseFloat(cc.cost) + cc.tax + cc.tip;
                        return cc.total
                    }
                    
                    
                    
                     cc.state_options = [
                        {amount:1.0169,name:"AK"},
                        {amount:1.0851,name:"AL"},
                        {amount:1.0919,name:"AR"},
                        {amount:1.0817,name:"AZ"},
                        {amount:1.0841,name:"CA"},
                        {amount:1.0739,name:"CO"},
                        {amount:1.0635,name:"CT"},
                        {amount:0,name:"DE"},
                        {amount:1.0662,name:"FL"},
                        {amount:1.0697,name:"GA"},
                        {amount:1.0435,name:"HI"},
                        {amount:1.0678,name:"IA"},
                        {amount:1.0603,name:"ID"},
                        {amount:1.0816,name:"IL"},
                        {amount:1.0700,name:"IN"},
                        {amount:1.0815,name:"KS"},
                        {amount:1.0600,name:"KY"},
                        {amount:1.0889,name:"LA"},
                        {amount:1.0625,name:"MA"},
                        {amount:1.0600,name:"MD"},
                        {amount:1.0550,name:"ME"},
                        {amount:1.0600,name:"MI"},
                        {amount:1.0719,name:"MN"},
                        {amount:1.0758,name:"MO"},
                        {amount:1.0700,name:"MS"},
                        {amount:0,name:"MT"},
                        {amount:1.0690,name:"NC"},
                        {amount:1.0655,name:"ND"},
                        {amount:1.0625,name:"NE"},
                        {amount:0,name:"NH"},
                        {amount:1.0697,name:"NJ"},
                        {amount:1.0726,name:"NM"},
                        {amount:1.0793,name:"NV"},
                        {amount:1.0847,name:"NY"},
                        {amount:1.0711,name:"OH"},
                        {amount:1.0872,name:"OK"},
                        {amount:0,name:"OR"},
                        {amount:1.0634,name:"PA"},
                        {amount:1.0700,name:"RI"},
                        {amount:1.0719,name:"SC"},
                        {amount:1.0583,name:"SD"},
                        {amount:1.0945,name:"TN"},
                        {amount:1.0825,name:"TX"},
                        {amount:1.0668,name:"UT"},
                        {amount:1.0563,name:"VA"},
                        {amount:1.0614,name:"VT"},
                        {amount:1.0888,name:"WA"},
                        {amount:1.0543,name:"WI"},
                        {amount:1.0607,name:"WV"},
                        {amount:1.0549,name:"WY"},
                    ];
                    
                    cc.statetax = cc.state_options[0];
                    
                    cc.tip_options = [
                        {amount:1.010,name:"10%"},
                        {amount:1.015,name:"15%"},
                        {amount:1.020,name:"20%"}
                    ];
                    
                    cc.tippercent = cc.tip_options[0];    
                        
            }
        );
```

### HTML Code

```
<div ng-controller="CostController as cc">
            <p>
                Cost: <input type="text" ng-model="cc.cost" placeholder="total bill" /><br/>
                State: <select ng-model="cc.tax" ng-options="s.name for s in cc.state_options" ng-change="cc.updatetax()"></select>
                Tip: <select ng-model="cc.tip" ng-options="s.name for s in cc.tip_options" ng-change="cc.updatetip()"></select>
                <input type="submit" ng-click="cc.update()" value="Calculate" />
            </p>
            <p>
                This is your bill: {{cc.cost|currency}}
            </p>
            <p>
                This is your subtotal: {{cc.subtotal|currency}}
            </p>
            <p>
                This is your total bill: {{cc.total|currency}}
            </p>
        </div>

```

