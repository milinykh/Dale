## Tale 2. Here comes the hero

A straighforward life story:

```xml
<tale>
    <character id="john">
        <name value="John"/>
        <gender value="male"/>
        <age value="P18"/>
        <maxAge value="P85Y"/>
    </character>
    <end>
        <character ref="john">
            <isAlive value="false"/>
        </character>
    </end>
</tale>
```

NOTE: All characters are alive by default, unless their `age` is equal to their `maxAge`.

Not so straighforward life story:

```xml
<tale>
    <character id="john">
        <name value="John"/>
        <gender value="male"/>
        <age value="P18Y"/>
        <maxAge minValue="P60Y" maxValue="P100Y"/>
    </character>
    <end>
        <character ref="john">
            <isAlive value="false"/>
        </character>
    </end>
</tale>
```

NOTE: Player doesn't know actual maximum age of a character. So, unless `maxAge` is specified as a sigle value, player has to take its randomization into account.

Player character's life story (not so different so far):

```xml
<tale>
    <character id="john">
        <name value="John"/>
        <gender value="male"/>
        <age value="P18"/>
        <maxAge value="P85Y"/>
        <isPlayer value="true"/>
    </character>
    <end>
        <character ref="john">
            <isAlive value="false"/>
        </character>
    </end>
</tale>
```

NOTES:
1. It's fine to have none or more than one player character.
2. Character's `isPlayer` property can be chnaged in a course of a tale.



