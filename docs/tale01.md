## Tale 1. Nothing but time

Tale without an end:

```xml
<tale>
    <begin>
        <time value="0154-04-12T12:00"/>
    </begin>
    <end>
    </end>
</tale>
```

Tale with an end:

```xml
<tale>
    <begin>
        <time value="0154-04-12T12:00"/>
    </begin>
    <end>
        <time value="0154-04-15T12:00"/>
    </end>
</tale>
```

Begin time can be randominzed in specified range:

```xml
<tale>
    <begin>
        <time minValue="0154-04-12T12:00" maxValue="0154-04-13T12:00"/>
    </begin>
    <end>
        <time value="0154-04-15T12:00"/>
    </end>
</tale>
```

End time can also be randominzed in specified range:

```xml
<tale>
    <begin>
        <time value="0154-04-12T12:00"/>
    </begin>
    <end>
        <time minValue="0154-04-15T12:00" maxValue="0154-04-17T12:00"/>
    </end>
</tale>
```

The range's borders are inclusive by default, but this behaviour can be changed (doesn't make much sense for time, but is quite useful for other data types):

```xml
<tale>
    <begin>
        <time value="0154-04-12T12:00"/>
    </begin>
    <end>
        <time minValue="0154-04-15T12:00" maxValue="0154-04-17T12:00"
              minInclusive="false" maxInclusive="false"/>
    </end>
</tale>
```

It's also possible to specify a set of possible times start/end times:

```xml
<tale>
    <begin>
        <time>
            <value>0154-04-12T12:00</value>
            <value>0154-04-12T16:00</value>
            <value>0154-04-13T09:00</value>
        </time>
    </begin>
    <end>
        <time value="0154-04-15T12:00"/>
    </end>
</tale>
```

Values of the set can be weighted:

```xml
<tale>
    <begin>
        <time>
            <value weight="10">0154-04-12T12:00</value>
            <value weight="10">0154-04-12T16:00</value>
            <value weight="15">0154-04-13T09:00</value>
        </time>
    </begin>
    <end>
        <time value="0154-04-15T12:00"/>
    </end>
</tale>
```


Sets and ranges can be combined:

```xml
<tale>
    <begin>
        <time>
            <value>0154-04-12T12:00</value>
            <value>0154-04-12T16:00</value>
            <range minValue="0154-04-13T09:00" maxValue="0154-04-13T18:00"/>
        </time>
    </begin>
    <end>
        <time value="0154-04-15T12:00"/>
    </end>
</tale>
```

Weights are applicable to combinations as well:

```xml
<tale>
    <begin>
        <time>
            <value weight="1">0154-04-12T12:00</value>
            <value weight="5">0154-04-12T16:00</value>
            <range weight="2" minValue="0154-04-13T09:00" maxValue="0154-04-13T18:00"/>
        </time>
    </begin>
    <end>
        <time value="0154-04-15T12:00"/>
    </end>
</tale>
```

It's allowed to specify duration instead of exact end time:

```xml
<tale>
    <begin>
        <time value="0154-04-12T12:00"/>
    </begin>
    <end>
        <duration value="P1DT10H"/>
    </end>
</tale>
```

Ranges and sets as well as their combinations can be used for the duration as well.

One more interesting example:

```xml
<tale>
    <chapter>
        <begin>
            <time value="0154-04-12T12:00"/>
        </begin>
        <end>
            <time minValue="0154-04-13T12:00" maxValue="0154-04-13T22:00"/>
        </end>
    </chapter>
    <chapter>
        <end>
            <time value="0154-04-15T12:00"/>
        </end>
    </chapter>
</tale>
```

