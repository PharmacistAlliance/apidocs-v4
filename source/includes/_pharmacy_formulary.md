## Pharmacy Formulary

> Example request to determine drug coverage using drug name:

```python
pd.pharmacy_formulary(trading_partner_id='medicare_national', plan_number='S0522034', drug='simvastatin')
```

```ruby
pd.pharmacy_formulary(trading_partner_id: 'medicare_national', plan_number: 'S0522034', drug: 'simvastatin')
```

```csharp
pd.pharmacyFormulary(
                      new Dictionary<string, string> {
                        {"trading_partner_id", "medicare_national"},
                        {"plan_number", "S0522034"},
                        {"drug",  "simvastatin"}
                    });
```

```java
Map<String, Object> params = new HashMap<String, Object>();
params.put("trading_partner_id", "medicare_national");
params.put("plan_number", "S0522034");
params.put("drug", "simvastatin");
Map<String, Object> response = pd.pharmacyFormulary(params);
```

> Example request to determine drug coverage using NDC:

```python
pd.pharmacy_formulary(trading_partner_id='medicare_national', plan_number='S0522034', ndc='00071101968')
```

```ruby
pd.pharmacy_formulary(trading_partner_id: 'medicare_national', plan_number: 'S0522034', ndc: '00071101968')
```

```csharp
pd.pharmacyFormulary(
                      new Dictionary<string, string> {
                        {"trading_partner_id", "medicare_national"},
                        {"plan_number", "S0522034"},
                        {"ndc",  "00071101968"}
                    });
```

```java
Map<String, Object> params = new HashMap<String, Object>();
params.put("trading_partner_id", "medicare_national");
params.put("plan_number", "S0522034");
params.put("ndc", "00071101968");
Map<String, Object> response = pd.pharmacyFormulary(params);
```

> Sample Pharmacy Formulary API response when searching for a drug name (SIMVASTATIN) : 

```json
{
    "data": [
        {
            "drug": "SIMVASTATIN 40 MG TABLET", 
            "prior_auth": false, 
            "quantity_limit": false, 
            "step_therapy": false, 
            "tier": 1, 
            "tier_name": "preferred generic",
            "mail": {
                "ins_pay_90_day": {
                    "amount": "3.89", 
                    "currency": "USD"
                }, 
                "oop_90_day": {
                    "amount": "3.00", 
                    "currency": "USD"
                }, 
                "total_cost_90_day": {
                    "amount": "6.89", 
                    "currency": "USD"
                }
            }, 
            "retail": {
                "ins_pay_30_day": {
                    "amount": "1.60", 
                    "currency": "USD"
                }, 
                "oop_30_day": {
                    "amount": "1.00", 
                    "currency": "USD"
                }, 
                "total_cost_30_day": {
                    "amount": "2.60", 
                    "currency": "USD"
                }
            }
        }, 
        {
            "drug": "SIMVASTATIN 20 MG TABLET",
            "prior_auth": false, 
            "quantity_limit": false, 
            "step_therapy": false, 
            "tier": 1, 
            "tier_name": "preferred generic",
            "mail": {
                "ins_pay_90_day": {
                    "amount": "2.33", 
                    "currency": "USD"
                }, 
                "oop_90_day": {
                    "amount": "3.00", 
                    "currency": "USD"
                }, 
                "total_cost_90_day": {
                    "amount": "5.33", 
                    "currency": "USD"
                }
            }, 
            "retail": {
                "ins_pay_30_day": {
                    "amount": "1.07", 
                    "currency": "USD"
                }, 
                "oop_30_day": {
                    "amount": "1.00", 
                    "currency": "USD"
                }, 
                "total_cost_30_day": {
                    "amount": "2.07", 
                    "currency": "USD"
                }
            }
        }, 
        {
            "drug": "SIMVASTATIN 5 MG TABLET", 
            "prior_auth": false, 
            "quantity_limit": false, 
            "step_therapy": false, 
            "tier": 1, 
            "tier_name": "preferred generic",
            "mail": {
                "ins_pay_90_day": {
                    "amount": "2.38", 
                    "currency": "USD"
                }, 
                "oop_90_day": {
                    "amount": "3.00", 
                    "currency": "USD"
                }, 
                "total_cost_90_day": {
                    "amount": "5.38", 
                    "currency": "USD"
                }
            }, 
            "retail": {
                "ins_pay_30_day": {
                    "amount": "1.07", 
                    "currency": "USD"
                }, 
                "oop_30_day": {
                    "amount": "1.00", 
                    "currency": "USD"
                }, 
                "total_cost_30_day": {
                    "amount": "2.07", 
                    "currency": "USD"
                }
            }
        }, 
        {
            "drug": "SIMVASTATIN 80 MG TABLET", 
            "limit_amount": "30", 
            "limit_days": 30, 
            "prior_auth": false, 
            "quantity_limit": true, 
            "step_therapy": false, 
            "tier": 1, 
            "tier_name": "preferred generic",
            "mail": {
                "ins_pay_90_day": {
                    "amount": "7.41", 
                    "currency": "USD"
                }, 
                "oop_90_day": {
                    "amount": "3.00", 
                    "currency": "USD"
                }, 
                "total_cost_90_day": {
                    "amount": "10.41", 
                    "currency": "USD"
                }
            }, 
            "retail": {
                "ins_pay_30_day": {
                    "amount": "2.80", 
                    "currency": "USD"
                }, 
                "oop_30_day": {
                    "amount": "1.00", 
                    "currency": "USD"
                }, 
                "total_cost_30_day": {
                    "amount": "3.80", 
                    "currency": "USD"
                }
            }
        }, 
        {
            "drug": "SIMVASTATIN 10 MG TABLET",
            "prior_auth": false, 
            "quantity_limit": false, 
            "step_therapy": false, 
            "tier": 1, 
            "tier_name": "preferred generic",
            "mail": {
                "ins_pay_90_day": {
                    "amount": "2.14", 
                    "currency": "USD"
                }, 
                "oop_90_day": {
                    "amount": "3.00", 
                    "currency": "USD"
                }, 
                "total_cost_90_day": {
                    "amount": "5.14", 
                    "currency": "USD"
                }
            }, 
            "retail": {
                "ins_pay_30_day": {
                    "amount": "1.00", 
                    "currency": "USD"
                }, 
                "oop_30_day": {
                    "amount": "1.00", 
                    "currency": "USD"
                }, 
                "total_cost_30_day": {
                    "amount": "2.00", 
                    "currency": "USD"
                }
            }
        }
    ]
}
```

> Sample Pharmacy Formulary API response when searching by NDC (00071101968) :

```json
{
    "data": [
        {
            "drug": "LYRICA 225 MG CAPSULE",
            "limit_amount": "60", 
            "limit_days": 30, 
            "prior_auth": false, 
            "quantity_limit": true, 
            "step_therapy": false, 
            "tier": 3, 
            "tier_name": "preferred brand",
            "mail": {
                "ins_pay_90_day": {
                    "amount": "793.09", 
                    "currency": "USD"
                }, 
                "oop_90_day": {
                    "amount": "198.27", 
                    "currency": "USD"
                }, 
                "total_cost_90_day": {
                    "amount": "991.36", 
                    "currency": "USD"
                }
            }, 
            "retail": {
                "ins_pay_30_day": {
                    "amount": "274.34", 
                    "currency": "USD"
                }, 
                "oop_30_day": {
                    "amount": "68.58", 
                    "currency": "USD"
                }, 
                "total_cost_30_day": {
                    "amount": "342.92", 
                    "currency": "USD"
                }
            }
        }
    ]
}
```

> Sample Pharmacy Formulary API response including plan info :

```json
"data" : {
        "drug": "VIMPAT 200 MG/20 ML VIAL", 
        "mail": {
            "ins_pay_90_day": {
                "amount": "1091.30", 
                "currency": "USD"
            }, 
            "oop_90_day": {
                "amount": "892.89", 
                "currency": "USD"
            }, 
            "total_cost_90_day": {
                "amount": "1984.19", 
                "currency": "USD"
            }
        }, 
        "plan": {
            "deductible": {
                "amount": "0.00", 
                "currency": "USD"
            }, 
            "initial_coverage_limit": {
                "amount": "3310.00", 
                "currency": "USD"
            }, 
            "mail": {
                "tier_one_90_day_copay": {
                    "amount": "7.50", 
                    "currency": "USD"
                }, 
                "tier_three_90_day_copay": {
                    "amount": "110.00", 
                    "currency": "USD"
                }, 
                "tier_two_90_day_copay": {
                    "amount": "30.00", 
                    "currency": "USD"
                }
            }, 
            "plan_name": "SilverScript Choice (PDP)", 
            "plan_number": "S5601026", 
            "premium": {
                "amount": "26.00", 
                "currency": "USD"
            }, 
            "retail": {
                "tier_one_30_day_copay": {
                    "amount": "3.00", 
                    "currency": "USD"
                }, 
                "tier_three_30_day_copay": {
                    "amount": "44.00", 
                    "currency": "USD"
                }, 
                "tier_two_30_day_copay": {
                    "amount": "12.00", 
                    "currency": "USD"
                }
            }, 
            "trading_partner_id": "medicare_national"
        }, 
        "prior_auth": false, 
        "quantity_limit": false, 
        "retail": {
            "ins_pay_30_day": {
                "amount": "363.96", 
                "currency": "USD"
            }, 
            "oop_30_day": {
                "amount": "297.79", 
                "currency": "USD"
            }, 
            "total_cost_30_day": {
                "amount": "661.75", 
                "currency": "USD"
            }
        }, 
        "step_therapy": false, 
        "tier": 4, 
        "tier_name": "non-preferred brand"
}
```

The Pharmacy Formulary Endpoint allows a deep dive into the member’s drug benefit. It returns details about what medications are covered in the formulary.  

A formulary is a list of medications that are approved for coverage by an insurance company. Drugs on a formulary are usually grouped into tier levels. The tier that the medication falls in determines the member’s copay. Most plans have between 3 to 5 tiers. The lower the tier, the less expensive the copay. Lower tiers are usually generic medication, middle tiers are brand medications, and the highest tier is usually reserved for specialty medications. 

This endpoint returns tier level and restrictions such as prior authorization, step therapy, and quantity limit. Only Medicare Part C and D plans are currently available.

Medications can also have restrictions on their coverage such as prior authorization, step therapy, and quantity limit.

| Endpoint            | HTTP Method | Description                        |
|:--------------------|:------------|:-----------------------------------|
| /pharmacy/formulary | GET         | Determine drug coverage for member |

To use the Pharmacy Formulary Endpoint with a Medicare member, you will need the plan number. This is the contract ID (ex. S1234) + Plan's Plan Benefit Package (PBP) Number PBP number (ex. 001) concatenated together in that order. There are several ways to get this number. The plan number may be on the member’s insurance card. If not, you can use an NCPDP E1 eligibility check or PokitDok’s Eligibility Endpoint. With the Eligibility Endpoint, Medicare members with Part D coverage will have pharmacy.is_eligible set to true and the pharmacy.plan_number will contain their Medicare Part D plan_number. Note: Your NPI must be registered with Medicare to check eligibility. 
 
A medication for which coverage is being determined will need to be specified. This can be done using the drug name, NDC, or RXCUI. A drug name can include the name of the medication, strength, and form. For example, SIMVASTATIN 10 MG TABLET. Simvastatin is the drug name. 10 MG is the strength. Simvastatin can come in other strengths (5mg, 10mg, 20mg, 40mg, and 80mg). The form of this medication is tablet. Some drugs will come in multiple forms. Other examples are capsule, solution, suspension, lotion, cream, etc. The brand name of simvastatin is Zocor. You can search for a drug with just the brand or generic name or any combination of drug +/- strength +/- form.

The Pharmacy Formulary Endpoint also accepts national drug code number (NDC). The NDC is a unique 11-digit, 3-segment number used to identify a specific drug product. The segments identify the manufacturer (first 5 numbers), product (middle 4 numbers), and package (last 2 numbers). An alternative way to lookup drug coverage is by using the NDC. One medication can have multiple NDC numbers. For example, simvastatin 10 mg tablets can be supplied to the pharmacy in a 100 count and 1000 count bottle. Both of these will have different NDC numbers even though the same drug is in each of the bottles. Simvastatin from different generic manufacturers will have different NDC numbers. 

Medicare drug plans have different phases of coverage, including deductible, initial coverage, gap coverage, and catastrophic coverage. Each phase has a different out of pocket cost for covered medications. The out of pocket costs included in the Pharmacy Formulary Endpoint are for the member during the Initial Coverage Phase.

Out of pocket costs for medications are based on 30 day supply at retail or 90 day supply at mail order pharmacies. Some medication isn’t taken continuously, ex. antibiotics. For those medications, the member would just pay one 30 day supply copay. 

In some cases, the member’s copay will be more than the total cost of the drug. In these situations, the actual amount the member will pay will depend on the pharmacy where they fill the prescription. For example, if the member’s copay is $10 and the drug only costs $4, the pharmacy could decide to charge the member the full $10, or the actual drug price of $4. If the copay is more expensive than the actual cost of the drug, the API will return the actual cost.

The field include_plans may be used if you would like to include an overview of the pharmacy plan information. This will add a new field to each drug document in the response.

The /pharmacy/formulary endpoint accepts the following parameters:

| Field              | Type     | Description                                                                                                                                                    |
|:-------------------|:---------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| trading_partner_id | {string} | Unique id for the intended [trading partner](https://platform.pokitdok.com/documentation/v4/#trading-partners), as specified by the Trading Partners endpoint. |
| plan_number        | {string} | Member’s plan identification number. Note: If unknown can use X12 270/271 eligibility                                                                          |
| drug               | {string} | Name of medication, strength, and form. Note: Strength and form are optional                                                                                   |
| ndc                | {string} | National drug code: a unique 11-digit, 3-segment number used to identify medication                                                                            |
| rxcui | {string} | An RxNorm concept unique identifier for a drug  |
| include_plan | {boolean} | If set to true, will return pharmacy plan info in response |

The /pharmacy/formulary response contains the following parameters:

| Field                 | Type      | Description                                                                                        |
|:----------------------|:----------|:---------------------------------------------------------------------------------------------------|
| drug                  | {string}  | The full drug name (name + strength + form)                                                        |
| tier                  | {short}   | The level the drug fall under on the formulary                                                     |
| tier_name             | {string}  | The name associated with the tier level                                                            |
| prior_auth            | {boolean} | Does the drug require a prior authorization?                                                       |
| step_therapy          | {boolean} | Does the drug require step therapy?                                                                |
| quantity_limit        | {boolean} | Does this drug have a quantity limit?                                                              |
| limit_amount | {string}  | Quantity limit amount associated with this drug. The unit of measure is specific to the drug type. |
| limit_days   | {integer} | Quantity limit days associated with this drug. E.g. 30                                             |
| retail.oop_30_day        | {string} | Estimated out of pocket cost for 30 day supply of drug at an in-network retail pharmacy                                                            |
| retail.total_cost_30_day | {string} | Estimated total cost of drug for 30 day supply of drug at an in-network retail pharmacy (average insurance negotiated rate with pharmacy)          |
| retail.ins_pay_30_day    | {string} | Estimated amount insurance covers for 30 day supply of drug at an in-network retail pharmacy    |
| mail.oop_90_day          | {string} | Estimated out of pocket cost for 90 day supply of drug at an in-network mail order pharmacy                                                        |
| mail.total_cost_90_day   | {string} | Estimated total cost of drug for 90 day supply of drug at an in-network mail order pharmacy (average insurance negotiated rate with pharmacy)      |
| mail.ins_pay_90_day      | {string} | Estimated amount insurance covers for 90 day supply of drug at an in-network mail order pharmacy |
