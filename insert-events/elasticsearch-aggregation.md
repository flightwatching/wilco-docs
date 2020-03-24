# elasticsearch aggregation

By default, the events are aggregated as documents in ELK if the bigdata option has been purchased.

In that case, all the events are pushed to ELK \(with a lag of 1 minute\)

## Document ID

In ELK all the documents have a unique ID. WILCO forces this ID. 

### Default behavior: merging the data

The **normal behavior** is to build the ID like `fwot.reg_computeddate`. This implies that if 2 events are on the same date for the same fwot, then the fields are merged together so that visualizations and correlations can be done. The drawback is that if the 2 events have a sample with the same parameter name, the latest insert will overwrite the previous one.

Event there are overwrites, this situation corresponds to physical behavior. If the paramter represents a physical measure, then it is impossible that at the same date, you have 2 different values.

```text
#event 1
{
fwot: FW-LUC
computeDate: 2010-04-09T00:00:00,
msg_id: 1234,
samples:[
  {
    name: 'A', value: 1
  },
  {
    name: 'C', value: 3
  },
]
```

```text
#event 2
{
fwot: FW-LUC
computeDate: 2010-04-09T00:00:00,
msg_id: 5678,
samples:[
  {
    name: 'B', value: 2
  },
  {
    name: 'C', value: 33
  },
]
```

```text
#document in ELK (only 1)
fwot: FW-LUC
computed_date: 2010-04-09T00:00:00
msg_id:5678
A:1
B:2
C:33
```

### Forcing the unicity of the documents

Nevertheless, you can override this to force the creation of one document per event. For example with the TECH LOG data, you can have several entries at the same date, but for different references. We allow this by mentionning a specific tag in the event: `BIGDATA_NO_AGG`

```text
#event 1
{
fwot: FW-LUC
computeDate: 2010-04-09T00:00:00,
msg_id: 1234,
tags: {id: BIGDATA_NO_AGG},
samples:[
  {
    name: 'A', value: 1
  },
  {
    name: 'C', value: 3
  },
]
```

```text
#event 2
{
fwot: FW-LUC
computeDate: 2010-04-09T00:00:00,
msg_id: 5678,
tags: {id: BIGDATA_NO_AGG},
samples:[
  {
    name: 'B', value: 2
  },
  {
    name: 'C', value: 33
  },
]
```

```text
#documents in ELK
fwot: FW-LUC
computed_date: 2010-04-09T00:00:00
msg_id:1234
A:1
C:3

fwot: FW-LUC
computed_date: 2010-04-09T00:00:00
msg_id:5678
B:2
C:33

```

## Field Mapping



