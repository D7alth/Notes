
**MODEL:** dtmi:besx:meter:energy

| name                         | path                      | unit | value type |
| ---------------------------- | ------------------------- | ---- | ---------- |
| SelfEnergyANVoltage          | /ANVoltage                |      | unique     |
| SelfEnergyBNVoltage          | /BNVoltage                |      | unique     |
| SelfEnergyCNVoltage          | /CNVoltage                |      | unique     |
| SelfEnergyConsumption        | /TotalConsumption         | kWh  | aggregate  |
| SelfEnergyTotalPower         | /TotalActivePower         | kW   | unique     |
| SelfTotalPowerFactor         | /TotalPowerFactor         |      | unique     |
| SelfTotalActivePower         | /TotalActivePower         | kW   | unique     |
| SelfEnergyGeneration         | /TotalGeneration          | kWh  | aggregte   |
| SelfTotalReactiveConsumption | /TotalReactiveConsumption | kWh  | aggregate  |
| SelfEnergyBCurrent           | /BCurrent                 | A    | unique     |
| SelfEnergyCCurrent           | /CCurrent                 | A    | unique     |
| SelfEnergyACurrent           | /ACurrent                 | A    | unique     |

**Para criar**

| name                        | path                     | unit | value type |
| --------------------------- | ------------------------ | ---- | ---------- |
| SelfAReactivePower          | /AReactivePower          |      | aggregate  |
| SelfBReactivePower          | /BReactivePower          |      | aggregate  |
| SelfCReactivePower          | /CReactivePower          |      | aggregate  |
| SelfTotalReactivePower      | /TotalReactivePower      |      | aggregate  |
|                             |                          |      |            |
| SelfAPowerAngle             | /APowerAngle             | °    | unique     |
| SelfBPowerAngle             | /BPowerAngle             | °    | unique     |
| SelfCPowerAngle             | /CPowerAngle             | °    | unique     |
|                             |                          |      |            |
| SelfAAparentPower           | /AAparentPower           |      | aggregate  |
| SelfBAparentPower           | /BAparentPower           |      | aggregate  |
| SelfCAparentPower           | /CAparentPower           |      | aggregate  |
| SelfTotalAparentPower       | /TotalAparentPower       |      | aggregate  |
|                             |                          |      |            |
| SelfABVoltage               | /ABVoltage               | V    | unique     |
|                             |                          |      |            |
| SelfAConsumption            | /AConsumption            | kWh  | aggregate  |
| SelfBConsumption            | /BConsumption            | kWh  | aggregate  |
| SelfCConsumption            | /CConsumption            | kWh  | aggregate  |
|                             |                          |      |            |
| SelfAGeneration             | /AGeneration             | kWh  | aggregate  |
| SelfBGeneration             | /BGeneration             | kWh  | aggregate  |
| SelfCGeneration             | /CGeneration             | kWh  | aggregate  |
|                             |                          |      |            |
| SelfAPowerFactor            | /APowerFactor            |      | aggregate  |
| SelfBPowerFactor            | /BPowerFactor            |      | aggregate  |
| SelfCPowerFactor            | /CPowerFactor            |      | aggregate  |
|                             |                          |      |            |
| SelfAReactiveConsumption    | /AReactiveConsumption    |      | aggregate  |
| SelfBReactiveConsumption    | /BReactiveConsumption    |      | aggregate  |
| SelfCReactiveConsumption    | /CReactiveConsumption    |      | aggregate  |
|                             |                          |      |            |
| SelfAReactiveGeneration     | /AReactiveGeneration     |      | aggregate  |
| SelfBReactiveGeneration     | /BReactiveGeneration     |      | aggregate  |
| SelfCReactiveGeneration     | /CReactiveGeneration     |      | aggregate  |
| SelfTotalReactiveGeneration | /TotalReactiveGeneration |      | aggregate  |
|                             |                          |      |            |
| SelfAActivePower            | /AActivePower            | kW   | aggregate  |
| SelfBActivePower            | /BActivePower            | kW   | aggregate  |
| SelfCActivePower            | /CActivePower            | kW   | aggregate  |
|                             |                          |      |            |
| SelfABVoltageAngle          | /ABVoltageAngle          | °    | unique     |
| SelfBCVoltageAngle          | /BCVoltageAngle          | °    | unique     |
| SelfCAVoltageAngle          | /CAVoltageAngle          | °    | unique     |
|                             |                          |      |            |
| SelfCAVoltage               | /CAVoltage               | °    | unique     |
|                             |                          |      |            |
| SelfInternTemperature       | /InternTemperature       | °C   | unique     |



| metric                             |
| ---------------------------------- |
| /APowerAngle                       |
| /AReactivePower                    |
| /CNVoltage                         |
| /ANVoltage                         |
| /AAparentPower                     |
| /TotalConsumption                  |
| /CPowerFactor                      |
| /AReactiveConsumption              |
| /ACurrent                          |
| /AReactiveGeneration               |
| /ConsumptionByType/AirConditioning |
| /CConsumption                      |
| /CAVoltageAngle                    |
| /CReactiveGeneration               |
| /AGeneration                       |
| /BNVoltage                         |
| /BCVoltageAngle                    |
| /CReactivePower                    |
| /CAVoltage                         |
| /CCurrent                          |
| /Heartbeat                         |
| /Frequency                         |
| /CPowerAngle                       |
| /InternTemperature                 |
| /CAparentPower                     |
| /BReactivePower                    |
| /TotalReactiveGeneration           |
| /BReactiveGeneration               |
| /TotalGeneration                   |
| /AActivePower                      |
| /BActivePower                      |
| /ConsumptionByType/OtherSystem     |
| /BAparentPower                     |
| /TotalAparentPower                 |
| /TotalPowerFactor                  |
| /TotalReactiveConsumption          |
| /APowerFactor                      |
| /ABVoltage                         |
| /AConsumption                      |
| /CReactiveConsumption              |
| /BPowerFactor                      |
| /TotalActivePower                  |
| /ABVoltageAngle                    |
| /BCVoltage                         |
| /BGeneration                       |
| /TotalReactivePower                |
| /BConsumption                      |
| /CGeneration                       |
| /BPowerAngle                       |
| /BCurrent                          |
| /CActivePower                      |
| /BReactiveConsumption              |







-----

**MODEL:** dtmi:besx:meter:call

![[Pasted image 20250115101804.png]]

-----

**MODEL:** dtmi:besx:meter:inverter

| name                           | path                | unit | value type |
| ------------------------------ | ------------------- | ---- | ---------- |
| SelfInverterExpectedGeneration | /ExpectedGeneration | kWh  | aggregate  |
| SelfInverterGeneration         | /TotalGeneration    | kWh  |            |
| SelfInverterPR                 | /PR                 | %    |            |
| SelfInverterNominalPower       | /NominalPower       | kWp  |            |
| SelfInverterActivePower        | /TotalActivePower   | kW   |            |

Criar 

| name                           | path                | unit | value type |
| ------------------------------ | ------------------- | ---- | ---------- |
| SelfinverterABVoltage          | /ABVoltage          | V    | unique     |
| SelfinverterBCVoltage          | /BCVoltage          | V    | unique     |
| SelfinverterCAVoltage          | /CAVoltage          | V    | unique     |
| SelfinverterDCVoltage          | /DCVoltage          | V    | unique     |
|                                |                     |      |            |
| SelfinverterANVoltage          | /ANVoltage          | V    | unique     |
| SelfinverterBNVoltage          | /BNVoltage          | V    | unique     |
| SelfinverterCNVoltage          | /CNVoltage          | V    | unique     |
|                                |                     |      |            |
| SelfinverterACurrent           | /ACurrent           | A    | unique     |
| SelfinverterBCurrent           | /BCurrent           | A    | unique     |
| SelfinverterCCurrent           | /CCurrent           | A    | unique     |
|                                |                     |      |            |
| SelfinverterDCCurrent          | /DCCurrent          | A    | unique     |
|                                |                     |      |            |
| SelfinverterDCPower            | /DCPower            |      | aggregate  |
|                                |                     |      |            |
| SelfinverterTemperature        | /Temperature        | °C   | unique     |
|                                |                     |      |            |
| SelfinverterTotalAparentPower  | /TotalAparentPower  |      | aggregate  |
|                                |                     |      |            |
| SelfinverterTotalPowerFactor   | /TotalPowerFactor   |      | unique     |
|                                |                     |      |            |
| SelfinverterTotalReactivePower | /TotalReactivePower |      | aggregate  |


-----

**MODEL:** dtmi:besx:meter:water

| name                 | path              | unit | value type |
| -------------------- | ----------------- | ---- | ---------- |
| SelfWaterConsumption | /TotalConsumption | L    | aggregate  |

-----

**MODEL:** dtmi:besx:meter:gas

| name               | path              | unit | value type |
| ------------------ | ----------------- | ---- | ---------- |
| SelfGasConsumption | /TotalConsumption | m³   | aggregate  |

-----

**MODEL:** dtmi:besx:meter:reservoir

| name           | path   | unit | value type |
| -------------- | ------ | ---- | ---------- |
| SelfWaterLevel | /Level | %    | unique     |

**Para criar**

| name | path           | unit | value type |
| ---- | -------------- | ---- | ---------- |
|      | /AnalogReading |      |            |

-----

**MODEL:** dtmi:besx:meter:sound

| name             | path                     | unit | value type |
| ---------------- | ------------------------ | ---- | ---------- |
| SelfDecibelMeter | /LogarithmicMeanPressure |      | unique     |

Para criar

| name | path          | unit | value type |
| ---- | ------------- | ---- | ---------- |
|      | /MaxPressure  |      | unique     |
|      | /MeanPressure |      |            |
|      | /MinPressure  |      |            |

-----

**MODEL:** dtmi:besx:meter:volume

| name            | path                         | unit | value type |
| --------------- | ---------------------------- | ---- | ---------- |
| SelfVolumeMeter | /Items/GLP/CurrentPercentage | %    | unique     |

Para criar

| name             | path                    | unit | value type |
| ---------------- | ----------------------- | ---- | ---------- |
| SelfCurrentValue | /Items/GLP/CurrentValue |      | unique     |
| SelfMaxValue     | /Items/GLP/MaxValue     |      |            |

------

**MODEL:** dtmi:besx:meter:waste

| name            | path                         | unit | value type |
| --------------- | ---------------------------- | ---- | ---------- |
| SelfVolumeMeter | /Items/GLP/CurrentPercentage | %    | unique     |

Para criar

| name                          | path                                     | unit | value type |
| ----------------------------- | ---------------------------------------- | ---- | ---------- |
| SelfAceitavelTotalRecicled    | /ByType/aceitavel/TotalRecicled          |      |            |
| SelfAceitavelTotalValue       | /ByType/aceitavel/TotalValue             |      |            |
| SelfAceitavelTotalWeight      | /ByType/aceitavel/TotalWeight            |      |            |
| SelfAceitavelValuePerWeight   | /ByType/aceitavel/ValuePerWeight         |      |            |
| SelfAluminioTotalRecicled     | /ByType/Aluminio/TotalRecicled           |      |            |
| SelfAluminioTotalValue        | /ByType/Aluminio/TotalValue              |      |            |
| SelfAluminioTotalWeight       | /ByType/Aluminio/TotalWeight             |      |            |
| SelfAluminioValuePerWeight    | /ByType/Aluminio/ValuePerWeight          |      |            |
| SelfCocoTotalRecicled         | /ByType/Coco/TotalRecicled               |      |            |
| SelfCocoTotalValue            | /ByType/Coco/TotalValue                  |      |            |
| SelfCocoTotalWeight           | /ByType/Coco/TotalWeight                 |      |            |
| SelfCocoValuePerWeight        | /ByType/Coco/ValuePerWeight              |      |            |
| SelfCocoWeight                | /ByType/Coco/Weight                      |      |            |
| SelfCompostavelTotalRecicled  | /ByType/Compostavel/TotalRecicled        |      |            |
| SelfCompostavelTotalValue     | /ByType/Compostavel/TotalValue           |      |            |
| SelfCompostavelTotalWeight    | /ByType/Compostavel/TotalWeight          |      |            |
| SelfCompostavelValuePerWeight | /ByType/Compostavel/ValuePerWeight       |      |            |
| SelfCompostavelWeight         | /ByType/Compostavel/Weight               |      |            |
|                               | /ByType/Composta���?Щ�?/TotalWeight     |      |            |
| SelfIsoporTotalRecicled       | /ByType/Isopor/TotalRecicled             |      |            |
| SelfIsoporTotalValue          | /ByType/Isopor/TotalValue                |      |            |
| SelfIsoporTotalWeight         | /ByType/Isopor/TotalWeight               |      |            |
| SelfIsoporValuePerWeight      | /ByType/Isopor/ValuePerWeight            |      |            |
| SelfIsoporWeight              | /ByType/Isopor/Weight                    |      |            |
| SelfMadeiraTotalRecicled      | /ByType/Madeira/TotalRecicled            |      |            |
| SelfMadeiraTotalValue         | /ByType/Madeira/TotalValue               |      |            |
| SelfMadeiraTotalWeight        | /ByType/Madeira/TotalWeight              |      |            |
| SelfMadeiraValuePerWeight     | /ByType/Madeira/ValuePerWeight           |      |            |
| SelfMetalTotalRecicled        | /ByType/Metal/TotalRecicled              |      |            |
| SelfMetalTotalValue           | /ByType/Metal/TotalValue                 |      |            |
| SelfMetalTotalWeight          | /ByType/Metal/TotalWeight                |      |            |
| SelfMetalValuePerWeight       | /ByType/Metal/ValuePerWeight             |      |            |
| SelfMetalWeight               | /ByType/Metal/Weight                     |      |            |
| SelfMistoTotalRecicled        | /ByType/Misto/TotalRecicled              |      |            |
| SelfMistoTotalValue           | /ByType/Misto/TotalValue                 |      |            |
| SelfMistoTotalWeight          | /ByType/Misto/TotalWeight                |      |            |
| SelfMistoValuePerWeight       | /ByType/Misto/ValuePerWeight             |      |            |
| SelfMistoWeight               | /ByType/Misto/Weight                     |      |            |
| SelfOrganicoTotalRecicled     | /ByType/Organico/TotalRecicled           |      |            |
| SelfOrganicoTotalValue        | /ByType/Organico/TotalValue              |      |            |
| SelfOrganicoTotalWeight       | /ByType/Organico/TotalWeight             |      |            |
| SelfOrganicoValuePerWeight    | /ByType/Organico/ValuePerWeight          |      |            |
| SelfOutrosTotalRecicled       | /ByType/Outros/TotalRecicled             |      |            |
| SelfOutrosTotalValue          | /ByType/Outros/TotalValue                |      |            |
| SelfOutrosTotalWeight         | /ByType/Outros/TotalWeight               |      |            |
| SelfOutrosValuePerWeight      | /ByType/Outros/ValuePerWeight            |      |            |
| SelfPapelaoTotalRecicled      | /ByType/Papelao/TotalRecicled            |      |            |
| SelfPapelaoTotalValue         | /ByType/Papelao/TotalValue               |      |            |
| SelfPapelaoTotalWeight        | /ByType/Papelao/TotalWeight              |      |            |
| SelfPapelaoValuePerWeight     | /ByType/Papelao/ValuePerWeight           |      |            |
| SelfPetTotalRecicled          | /ByType/Pet/TotalRecicled                |      |            |
| SelfPetTotalValue             | /ByType/Pet/TotalValue                   |      |            |
| SelfPetTotalWeight            | /ByType/Pet/TotalWeight                  |      |            |
| SelfPetValuePerWeight         | /ByType/Pet/ValuePerWeight               |      |            |
| SelfPetWeight                 | /ByType/Pet/Weight                       |      |            |
|                               | /ByType/Plastico���?���?1/TotalRecicled  |      |            |
|                               | /ByType/Plastico���?���?1/TotalValue     |      |            |
|                               | /ByType/Plastico���?���?1/TotalWeight    |      |            |
|                               | /ByType/Plastico���?���?1/ValuePerWeight |      |            |
| SelfPlasticoTotalRecicled     | /ByType/Plastico/TotalRecicled           |      |            |
| SelfPlasticoTotalValue        | /ByType/Plastico/TotalValue              |      |            |
| SelfPlasticoTotalWeight       | /ByType/Plastico/TotalWeight             |      |            |
| SelfPlasticoValuePerWeight    | /ByType/Plastico/ValuePerWeight          |      |            |
| SelfPlasticoWeight            | /ByType/Plastico/Weight                  |      |            |
| SelfRejeitosTotalRecicled     | /ByType/Rejeitos/TotalRecicled           |      |            |
| SelfRejeitosTotalValue        | /ByType/Rejeitos/TotalValue              |      |            |
| SelfRejeitosTotalWeight       | /ByType/Rejeitos/TotalWeight             |      |            |
| SelfRejeitosValuePerWeight    | /ByType/Rejeitos/ValuePerWeight          |      |            |
| SelfRejeitosTotalRecicled     | /ByType/Rejeito/TotalRecicled            |      |            |
| SelfRejeitosTotalValue        | /ByType/Rejeito/TotalValue               |      |            |
| SelfRejeitosTotalWeight       | /ByType/Rejeito/TotalWeight              |      |            |
| SelfRejeitosValuePerWeight    | /ByType/Rejeito/ValuePerWeight           |      |            |
| SelfTecidoTotalRecicled       | /ByType/Tecido/TotalRecicled             |      |            |
| SelfTecidoTotalValue          | /ByType/Tecido/TotalValue                |      |            |
| SelfTecidoTotalWeight         | /ByType/Tecido/TotalWeight               |      |            |
| SelfTecidoValuePerWeight      | /ByType/Tecido/ValuePerWeight            |      |            |
| SelfTesteTotalRecicled        | /ByType/Teste/TotalRecicled              |      |            |
| SelfTesteTotalValue           | /ByType/Teste/TotalValue                 |      |            |
| SelfTesteTotalWeight          | /ByType/Teste/TotalWeight                |      |            |
| SelfTesteValuePerWeight       | /ByType/Teste/ValuePerWeight             |      |            |
| SelfVidroTotalRecicled        | /ByType/Vidro/TotalRecicled              |      |            |
| SelfVidroTotalValue           | /ByType/Vidro/TotalValue                 |      |            |
| SelfVidroTotalWeight          | /ByType/Vidro/TotalWeight                |      |            |
| SelfVidroValuePerWeight       | /ByType/Vidro/ValuePerWeight             |      |            |
| SelfVidroWeight               | /ByType/Vidro/Weight                     |      |            |
|                               | /TotalWeight                             |      |            |
|                               | /Type/Compostavel/Weight                 |      |            |


Vou criar 

| name                      | path                           | unit | value type |
| ------------------------- | ------------------------------ | ---- | ---------- |
| SelfRejeitoTotalRecicled  | /ByType/Rejeito/TotalRecicled  |      | aggregate  |
| SelfRejeitoTotalValue     | /ByType/Rejeito/TotalValue     |      | aggregate  |
| SelfRejeitoTotalWeight    | /ByType/Rejeito/TotalWeight    |      | aggregate  |
| SelfRejeitoValuePerWeight | /ByType/Rejeito/ValuePerWeight |      |            |
|                           |                                |      |            |



------

**MODEL:** dtmi:besx:meter:weather

| name             | path                     | unit | value type |
| ---------------- | ------------------------ | ---- | ---------- |
| SelfDecibelMeter | /LogarithmicMeanPressure |      | unique     |

Para criar

| name | path                  | unit | value type |
| ---- | --------------------- | ---- | ---------- |
|      | /DewPoint             | °C   | unique     |
|      | /InstantPrecipitation | mm   | unique     |


