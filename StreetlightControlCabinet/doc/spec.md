# Streetlight control cabinet

It represents equipment, usually on street, used to the automated control of a
group(s) of streetlights, i.e. one or more circuits.

## Data Model

The data model is defined as shown below:

-   `id` : Entity's unique identifier.

-   `type` : It must be equal to `StreetlightControlCabinet`.

-   `source` : A sequence of characters giving the source of the entity data.

    -   Attribute type: Property. [Text](https://schema.org/Text) or [URL](https://schema.org/URL)
    -   Optional

-   `dataProvider` : Specifies the URL to information about the provider of this
    information

    -   Attribute type: Property. [URL](https://schema.org/URL)
    -   Optional

-   `location` : Control cabinet's location represented by a GeoJSON point.

    -   Attribute type: GeoProperty. `geo:json`.
    -   Normative References:
        [https://tools.ietf.org/html/draft-ietf-geojson-03](https://tools.ietf.org/html/draft-ietf-geojson-03)
    -   Mandatory

-   `address` : Civic address where the control cabinet is located.

    -   Attribute type: Property. [Address](https://schema.org/address)
    -   Normative References:
        [https://schema.org/address](https://schema.org/address)
    -   Mandatory if `location` is not present.

-   `areaServed` : Higher level area to which the cabinet belongs to. It can be
    used to group per responsible, district, neighbourhood, etc.

    -   Normative References:
        [https://schema.org/areaServed](https://schema.org/areaServed)
    -   Optional

-   `serialNumber` : Serial number of the control cabinet.

    -   Attribute type: Property. [Text](https://schema.org/Text)
    -   Normative References:
        [https://schema.org/serialNumber](https://schema.org/serialNumber)
    -   Optional

-   `refStreetlightGroup` : Streetlight group(s) controlled.

    -   Attribute type: Property. List of references to entities of type
        [StreetlightGroup](../../StreetlightGroup/doc/spec.md).
    -   Mandatory

-   `brandName` : Name of the cabinet's brand.

    -   Attribute type: Property. [Text](https://schema.org/Text)
    -   See also: [https://schema.org/brand](https://schema.org/brand)
    -   Optional

-   `modelName` : Name of the cabinet's model.

    -   Attribute type: Property. [Text](https://schema.org/Text)
    -   See also: [https://schema.org/model](https://schema.org/model)
    -   Optional

-   `manufacturerName` : Name of the cabinet's manufacturer.

    -   Attribute type: Property. [Text](https://schema.org/Text)
    -   See also: [https://schema.org/model](https://schema.org/manufacturer)
    -   Optional

-   `cupboardMadeOf` : Material the cabinet's cupboard is made of.

    -   Attribute type: Property. [Text](https://schema.org/Text)
    -   Allowed values: one Of (`plastic`, `metal`, `concrete`, `other`)
    -   Optional

-   `features` : A list of cabinet controller features.

    -   Attribute type: Property. List of [Text](https://schema.org/Text)
    -   Allowed Values: Those technical values considered meaningful by
        applications.
        -   `astronomicalClock` . The control cabinet includes an astronomical
            clock to deal with switching hours.
        -   `individualControl`. The control cabinet allows to control street
            lights individually.

-   `compliantWith`. A list of standards to which the cabinet controller is
    compliant with (ex. `IP54`)

    -   AttributeType: List of [Text](https://schema.org/Text).
    -   Optional

-   `annotations` : A field reserved for annotations (incidences, remarks,
    etc.).

    -   Attribute type: Property. List of [Text](https://schema.org/Text)
    -   Optional

-   `refDevice` : Reference to the device(s) used to monitor this control
    cabinet.

    -   Attribute type: Relationship. List of Reference to entity(ies) of type
        [Device](../../../Device/Device/doc/spec.md)
    -   Optional

-   `dateModified` : Last update timestamp of this entity.

    -   Attribute type: Property. [DateTime](https://schema.org/DateTime)
    -   Read-Only. Automatically generated.

-   `dateServiceStarted` : Date at which the cabinet controller started giving
    service.

    -   Attribute type: Property. [DateTime](https://schema.org/DateTime)
    -   Optional

-   `dateLastProgramming` : Date at which there was a programming operation over
    the cabinet.

    -   Attribute type: Property. [DateTime](https://schema.org/DateTime)
    -   Optional

-   `nextActuationDeadline` : Deadline for next actuation to be performed
    (programming, testing, etc.).

    -   Attribute type: Property. [DateTime](https://schema.org/DateTime)
    -   Optional

-   `responsible` : Responsible for the cabinet controller, i.e. entity in
    charge of actuating (programming, etc.).

    -   Attribute type: Property. [Text](http://schema.org/Text)
    -   Optional

-   `workingMode` : Working mode for this cabinet controller.

    -   Attribute type: Property. [Text](http://schema.org/Text)
    -   Allowed values:
        -   `automatic` : The cabinet controller decides automatically when
            light groups are switched on and off. Manual operation is not
            allowed.
        -   `manual` : Human intervention is required for switching on and off.
        -   `semiautomatic` : The same as `automatic` but in this case manual
            intervention is allowed.
    -   Mandatory

-   `maximumPowerAvailable` : The maximum power available (by contract) for the
    circuits controlled by this cabinet.

    -   Attribute type: Property. [Number](http://schema.org/Number)
    -   Default unit: Kilowatts (kW)
    -   Optional

-   `energyConsumed` : Energy consumed by the circuits controlled since metering
    started (since `dateMeteringStarted`).

    -   Attribute type: Property. [Number](https://schema.org/Number)
    -   Default unit: Kilowatts per hour (kWh).
    -   Attribute metadata:
        -   `timestamp`: Timestamp when the last update of the attribute
            happened.
            -   Type: [DateTime](http://schema.org/DateTime)
    -   Optional

-   `energyCost` : Cost of the energy consumed by the circuits controlled since
    the metering start date (`dateMeteringStarted`).

    -   Attribute type: Property. [Number](https://schema.org/Number)
    -   Default currency: Euros. (Other currencies might be expressed using a
        metadata attribute)
    -   Attribute metadata:
        -   `timestamp`: Timestamp when the last update of the attribute
            happened.
            -   Type: [DateTime](http://schema.org/DateTime)
    -   Optional

-   `reactiveEnergyConsumed` : Energy consumed (with regards to reactive power)
    by circuits since the metering start date (`dateMeteringStarted`).

    -   Attribute type: Property. [Number](https://schema.org/Number)
        -   Default unit: KiloVolts-Ampere-Reactive per hour (kVArh).
    -   Attribute metadata:
        -   `timestamp`: Timestamp when the last update of the attribute
            happened.
            -   Type: [DateTime](http://schema.org/DateTime)
    -   Optional

-   `dateMeteringStarted` : The starting date for metering energy consumed.

    -   Attribute type: Property. [DateTime](https://schema.org/DateTime)
    -   Mandatory if `energyConsumed` is present.

-   `lastMeterReading` : Value of the last reading obtained from the energy
    consumed metering system.

    -   Attribute type: Property. [Number](https://schema.org/Number)
    -   Default unit: Kilowatts per hour (kWh).
    -   Attribute metadata:
        -   `timestamp`: Timestamp which reflects the date and time at which the
            referred reading was obtained.
            -   Type: [DateTime](http://schema.org/DateTime)
    -   Optional

-   `meterReadingPeriod` : The periodicity of energy consumed meter readings in
    days.

    -   Attribute type: Property. [Number](http://schema.org/Number)
    -   Optional

-   `frequency` : The working frequency of the circuit.

    -   Attribute type: Property. [Number](http://schema.org/Number)
    -   Default unit: Hertz (Hz)
    -   Optional

-   `totalActivePower` : Active power currently consumed (counting all phases).

    -   Attribute type: Property. [Number](http://schema.org/Number)
    -   Default unit: KiloWatts (kW).
    -   Attribute metadata:
        -   `timestamp`: Timestamp when the last update of the attribute
            happened.
            -   Type: [DateTime](http://schema.org/DateTime)
    -   Optional

-   `totalReactivePower` : Reactive power currently consumed (counting all
    phases).

    -   Attribute type: Property. [Number](http://schema.org/Number)
    -   Default unit: KiloVolts-Ampere-Reactive (kVArh).
    -   Attribute metadata:
        -   `timestamp`: Timestamp when the last update of the attribute
            happened.
            -   Type: [DateTime](http://schema.org/DateTime)
    -   Optional

-   `activePowerR` : Active power consumed in R phase.

    -   Attribute Type: Property. [Number](http://schema.org/Number)
    -   Default unit: Kilowatts (kW)
    -   Attribute metadata:
        -   `timestamp`: Timestamp when the last update of the attribute
            happened.
            -   Type: [DateTime](http://schema.org/DateTime)
    -   Optional
    
-   `activePowerS` : Active power consumed in S phase.

    -   Attribute Type: Property. [Number](http://schema.org/Number)
    -   Default unit: Kilowatts (kW)
    -   Attribute metadata:
        -   `timestamp`: Timestamp when the last update of the attribute
            happened.
            -   Type: [DateTime](http://schema.org/DateTime)
    -   Optional
    
-   `activePowerT` : Active power consumed in T phase.

    -   Attribute Type: Property. [Number](http://schema.org/Number)
    -   Default unit: Kilowatts (kW)
    -   Attribute metadata:
        -   `timestamp`: Timestamp when the last update of the attribute
            happened.
            -   Type: [DateTime](http://schema.org/DateTime)
    -   Optional    

-   `reactivePowerR` : Reactive power in R phase.

    -   Attribute Type: Property. [Number](http://schema.org/Number)
    -   Default unit: KiloVolts-Ampere-Reactive (kVArh)
    -   Attribute metadata:
        -   `timestamp`: Timestamp when the last update of the attribute
            happened.
            -   Type: [DateTime](http://schema.org/DateTime)
    -   Optional

-   `reactivePowerS` : Reactive power in S phase.

    -   Attribute Type: Property. [Number](http://schema.org/Number)
    -   Default unit: KiloVolts-Ampere-Reactive (kVArh)
    -   Attribute metadata:
        -   `timestamp`: Timestamp when the last update of the attribute
            happened.
            -   Type: [DateTime](http://schema.org/DateTime)
    -   Optional
    
-   `reactivePowerT` : Reactive power in T phase.
 
    -   Attribute Type: Property. [Number](http://schema.org/Number)
    -   Default unit: KiloVolts-Ampere-Reactive (kVArh)
    -   Attribute metadata:
        -   `timestamp`: Timestamp when the last update of the attribute
            happened.
            -   Type: [DateTime](http://schema.org/DateTime)
    -   Optional
    
-   `powerFactorR` : Power factor for phase R.

    -   Attribute type: Property. [Number](http://schema.org/Number)
    -   Allowed values: A number between -1 and 1.
    -   Attribute metadata:
        -   `timestamp`: Timestamp when the last update of the attribute
            happened.
            -   Type: [DateTime](http://schema.org/DateTime)
    -   Optional

-   `powerFactorS` : Power factor for phase S.

    -   Attribute type: Property. [Number](http://schema.org/Number)
    -   Allowed values: A number between -1 and 1.
    -   Attribute metadata:
        -   `timestamp`: Timestamp when the last update of the attribute
            happened.
            -   Type: [DateTime](http://schema.org/DateTime)
    -   Optional
    
-   `powerFactorT` : Power factor for phase T.

    -   Attribute type: Property. [Number](http://schema.org/Number)
    -   Allowed values: A number between -1 and 1.
    -   Attribute metadata:
        -   `timestamp`: Timestamp when the last update of the attribute
            happened.
            -   Type: [DateTime](http://schema.org/DateTime)
    -   Optional

-   `cosPhi` : "Cosin of phi" parameter.

    -   Attribute type: Property. [Number](http://schema.org/Number)
    -   Allowed values: A number between -1 and 1.
    -   Attribute metadata:
        -   `timestamp`: Timestamp when the last update of the attribute
            happened.
            -   Type: [DateTime](http://schema.org/DateTime)
    -   Optional

-   `intensityR` : Electric intensity in R phase.

    -   Attribute Type: Property. [Number](http://schema.org/Number)
    -   Default unit: Ampers (A)
    -   Attribute metadata:
        -   `timestamp`: Timestamp when the last update of the attribute
            happened.
            -   Type: [DateTime](http://schema.org/DateTime)
    -   Optional

-   `intensityS` : Electric intensity in S phase.

    -   Attribute Type: Property. [Number](http://schema.org/Number)
    -   Default unit: Ampers (A)
    -   Attribute metadata:
        -   `timestamp`: Timestamp when the last update of the attribute
            happened.
            -   Type: [DateTime](http://schema.org/DateTime)
    -   Optional
    
-   `intensityT` : Electric intensity in T phase.

    -   Attribute Type: Property. [Number](http://schema.org/Number)
    -   Default unit: Ampers (A)
    -   Attribute metadata:
        -   `timestamp`: Timestamp when the last update of the attribute
            happened.
            -   Type: [DateTime](http://schema.org/DateTime)
    -   Optional

-   `voltageR` : Electric tension in phase R.

    -   Attribute Type: Property. [Number](http://schema.org/Number)
    -   Default unit: Volts (V)
    -   Attribute metadata:
        -   `timestamp`: Timestamp when the last update of the attribute
            happened.
            -   Type: [DateTime](http://schema.org/DateTime)
    -   Optional
 
-   `voltageS` : Electric tension in phase S.

    -   Attribute Type: Property. [Number](http://schema.org/Number)
    -   Default unit: Volts (V)
    -   Attribute metadata:
        -   `timestamp`: Timestamp when the last update of the attribute
            happened.
            -   Type: [DateTime](http://schema.org/DateTime)
    -   Optional
    
-   `voltageT` : Electric tension in phase T.

    -   Attribute Type: Property. [Number](http://schema.org/Number)
    -   Default unit: Volts (V)
    -   Attribute metadata:
        -   `timestamp`: Timestamp when the last update of the attribute
            happened.
            -   Type: [DateTime](http://schema.org/DateTime)
    -   Optional

-   `thdrVoltageR` : Total harmonic distortion (R) of voltage in phase R.

    -   Attribute Type: Property. [Number](http://schema.org/Number)
    -   Allowed values: A number between 0 and 1.
    -   Optional
    
-   `thdrVoltageS` : Total harmonic distortion (S) of voltage in phase S.

    -   Attribute Type: Property. [Number](http://schema.org/Number)
    -   Allowed values: A number between 0 and 1.
    -   Optional
    
-   `thdrVoltageT` : Total harmonic distortion (T) of voltage in phase T.

    -   Attribute Type: Property. [Number](http://schema.org/Number)
    -   Allowed values: A number between 0 and 1.
    -   Optional

-   `thdrIntensityR` : Total harmonic distortion (R) of intensity in phase R.

    -   Attribute Type: Property. [Number](http://schema.org/Number)
    -   Allowed values: A number between 0 and 1.
    -   Optional
    
-   `thdrIntensityS` : Total harmonic distortion (S) of intensity in phase S.

    -   Attribute Type: Property. [Number](http://schema.org/Number)
    -   Allowed values: A number between 0 and 1.
    -   Optional
    
-   `thdrIntensityT` : Total harmonic distortion (T) of intensity in phase T.

    -   Attribute Type: Property. [Number](http://schema.org/Number)
    -   Allowed values: A number between 0 and 1.
    -   Optional

**Note**: JSON Schemas are intended to capture the data type and associated
constraints of the different Attributes, regardless their final representation
format in NGSI(v2, LD).

## Examples

### Normalized Example

Normalized NGSI response

```json
{
    "id": "streetlightcontrolcabinet:A45HGJK",
    "type": "StreetlightControlCabinet",
    "modelName": {
        "value": "Simatic S7 1200"
    },
    "lastMeterReading": {
        "value": 161237
    },
    "dateMeteringStarted": {
        "type": "DateTime",
        "value": "2013-07-07T15:05:59.408Z"
    },
    "dateLastProgramming": {
        "type": "DateTime",
        "value": "2016-07-08T16:04:30.201Z"
    },
    "refStreetlightGroup": {
        "type": "Relationship",
        "value": ["streetlightgroup:BG678", "streetlightgroup:789"]
    },
    "compliantWith": {
        "value": ["IP54"]
    },
    "intensityR": {
        "type": "Number",
        "value": 20.1
    },
    "intensityS": {
        "type": "Number",
        "value": 14.4
    },
    "intensityT": {
        "type": "Number",
        "value": 22
    },
    "workingMode": {
        "value": "automatic"
    },
    "energyConsumed": {
        "value": 162456
    },
    "meterReadingPeriod": {
        "value": 60
    },
    "cupboardMadeOf": {
        "value": "plastic"
    },
    "brandName": {
        "value": "Siemens"
    },
    "location": {
        "type": "geo:json",
        "value": {
            "type": "Point",
            "coordinates": [-3.164485591715449, 40.62785133667262]
        }
    },
    "reactivePowerR": {
        "type": "Number",
        "value": 45
    },
    "reactivePowerS": {
        "type": "Number",
        "value": 43.5
    },
    "reactivePowerT": {
        "type": "Number",
        "value": 42
    },
    "maximumPowerAvailable": {
        "value": 10
    }
}
```

### key-value pairs Example

Sample uses simplified representation for data consumers `?options=keyValues`

```json
{
    "id": "streetlightcontrolcabinet:A45HGJK",
    "type": "StreetlightControlCabinet",
    "location": {
        "type": "Point",
        "coordinates": [-3.164485591715449, 40.62785133667262]
    },
    "cupboardMadeOf": "plastic",
    "brandName": "Siemens",
    "modelName": "Simatic S7 1200",
    "refStreetlightGroup": ["streetlightgroup:BG678", "streetlightgroup:789"],
    "compliantWith": ["IP54"],
    "dateLastProgramming": "2016-07-08T16:04:30.201Z",
    "maximumPowerAvailable": 10,
    "energyConsumed": 162456,
    "dateMeteringStarted": "2013-07-07T15:05:59.408Z",
    "lastMeterReading": 161237,
    "meterReadingPeriod": 60,
    "intensityR": 20.1,
    "intensityS": 14.4,
    "intensityT": 22,
    "reactivePowerR": 45,
    "reactivePowerS": 43.5,
    "reactivePowerT": 42,
    "workingMode": "automatic"
}
```

### LD Example

Sample uses the NGSI-LD representation

```json
{
    "id": "urn:ngsi-ld:StreetlightControlCabinet:streetlightcontrolcabinet:A45HGJK",
    "type": "StreetlightControlCabinet",
    "modelName": {
        "type": "Property",
        "value": "Simatic S7 1200"
    },
    "lastMeterReading": {
        "type": "Property",
        "value": 161237
    },
    "dateMeteringStarted": {
        "type": "Property",
        "value": {
            "@type": "DateTime",
            "@value": "2013-07-07T15:05:59.408Z"
        }
    },
    "dateLastProgramming": {
        "type": "Property",
        "value": {
            "@type": "DateTime",
            "@value": "2016-07-08T16:04:30.201Z"
        }
    },
    "refStreetlightGroup": {
        "type": "Relationship",
        "object": [
            "urn:ngsi-ld:StreetlightGroup:streetlightgroup:BG678",
            "urn:ngsi-ld:StreetlightGroup:streetlightgroup:789"
        ]
    },
    "compliantWith": {
        "type": "Property",
        "value": ["IP54"]
    },
    "intensityR": {
        "type": "Property",
        "value": 20.1
    },
    "intensityS": {
        "type": "Property",
        "value": 14.4
    },
    "intensityT": {
        "type": "Property",
        "value": 22
    },    
    "workingMode": {
        "type": "Property",
        "value": "automatic"
    },
    "energyConsumed": {
        "type": "Property",
        "value": 162456
    },
    "meterReadingPeriod": {
        "type": "Property",
        "value": 60
    },
    "cupboardMadeOf": {
        "type": "Property",
        "value": "plastic"
    },
    "brandName": {
        "type": "Property",
        "value": "Siemens"
    },
    "location": {
        "type": "GeoProperty",
        "value": {
            "type": "Point",
            "coordinates": [-3.164485591715449, 40.62785133667262]
        }
    },
    "reactivePowerR": {
        "type": "Property", 
        "value": 45
    },
    "reactivePowerS": {
        "type": "Property",
        "value": 43.5
    },
    "reactivePowerT": {
        "type": "Property",
        "value": 42
    },   
    "maximumPowerAvailable": {
        "type": "Property",
        "value": 10
    },
    "@context": [
        "https://schema.lab.fiware.org/ld/context",
        "https://uri.etsi.org/ngsi-ld/v1/ngsi-ld-core-context.jsonld"
    ]
}
```

## Test it with a real service

## Open Issues

-   Should we create a `StreetlightControlCabinetModel` entity type?
-   Should we have the programming parameters as attribute of this entity?
    Advantage is that if programming is the same for all the controlled cicuits
    then there is no need to repeat the same parameters over multiple entities.
