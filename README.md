# OData V4 Service modules - MongoDB Connector 

Tools to transform OData requests to MQL syntax.

## Synopsis
The OData V4 MongoDB Connector provides functionality to convert the various types of OData segments
into MongoDB query objects, that you can execute over a MongoDB database.

## Potential usage scenarios

- Create high speed, standard compliant data sharing APIs

## Supported OData segments

For now **$filter**, **$select**, **$skip** and **$top**

Support for **$expand** is next.

### Supported $filter expressions

The [@odata/parser](https://github.com/Soontao/odata-v4-parser) layer supports 100% of the specification.
The Connector is supporting basic MongoDB queries.

*We are into creating a comprehensive feature availability chart for V1 release*

    mongodb query
       √ expression: $filter=contains(Name,'c')&$orderby=UnitPrice
       √ expression: $filter=contains(Name,'c')&$orderby=Name
       √ expression: $filter=contains(Description,'c')&$orderby=Name
   
     mongodb visitor
       √ expression: 1 eq 1
       √ expression: (1 eq 1) or (2 eq 2)
       √ expression 5.1.1.6.1: NullValue eq null
       √ expression 5.1.1.6.1: TrueValue eq true
       √ expression 5.1.1.6.1: FalseValue eq false
       √ expression 5.1.1.6.1: IntegerValue lt -128
       √ expression 5.1.1.6.1: DecimalValue eq 34.95
       √ expression 5.1.1.6.1: StringValue eq 'Say Hello,then go'
       √ expression 5.1.1.6.1: DurationValue eq duration'P12DT23H59M59.999999999999S'
       √ expression 5.1.1.6.1: DateValue eq 2012-12-03
       √ expression 5.1.1.6.1: DateTimeOffsetValue eq 2012-12-03T07:16:23Z
       √ expression 5.1.1.6.1: GuidValue eq 01234567-89ab-cdef-0123-456789abcdef
       √ expression 5.1.1.6.1: Int64Value eq 0
       √ expression 5.1.1.6.1: A eq INF
       √ expression 5.1.1.6.1: A eq 0.31415926535897931e1
       √ expression 5.1.1.1.2: A ne 1
       √ expression 5.1.1.1.3: A gt 2
       √ expression 5.1.1.1.4: A ge 3
       √ expression 5.1.1.1.5: A lt 2
       √ expression 5.1.1.1.6: A le 2
       √ expression 5.1.1.1.6: A/b eq 1
       √ expression  5.1.1.1.6: A eq '1%20%26%202%2B %2F'
       √ expression  5.1.1.1.6:  A eq '1/2|.*(?|\/)' // encode this before
       √ expression 5.1.1.3: (A/b eq 2) or (B/c lt 4) and ((E gt 5) or (E lt -1))
       √ expression 5.1.1.4.1: contains(A, 'BC')
       √ expression 5.1.1.4.1: contains(A, '%7C')
       √ expression 5.1.1.4.1: contains(A, '1%20%26%202') or contains(D, 'EF')
       √ expression 5.1.1.4.2: endswith(A, '%7C')
       √ expression 5.1.1.4.2: endswith(A, 'CD')
       √ expression 5.1.1.4.3: startswith(A, 'CD')
       √ expression 5.1.1.4.3: startswith(A, '%7C')
       √ expression 5.1.1.1.11: not endswith(Name,'ilk')

