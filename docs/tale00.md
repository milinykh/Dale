## Tale 0. Before it begins

* Every tale must have at least two sections: `begin` and `end`.
* It's fine for these sections to be empty. Everything is expected to have some reasonable default value.

Minmalistic neverending tale:

```xml
<tale>
    <begin>
        <!-- Initial state/changes of the tale. -->
    </begin>
    <end>
        <!-- Ending conditions of the tale. -->
    </end>
</tale>
```

This is also fine:

```xml
<tale>
</tale>
```

and basically equivalent to:

```xml
<tale>
    <begin>
    </begin>
    <end>
    </end>
</tale>
```

If it's not enough, then a tale can be subdiveded into chapters:

```xml
<tale>
    <chapter>
        <pre>
            <!-- Prerequisites of the chapter. -->
        </pre>
        <begin>
            <!-- Initial state/changes of the chapter. -->
        </begin>
        <end>
            <!-- Ending conditions of the chapter. -->
        </end>
        <post>
            <!-- Post state/changes of the chapter. -->
        </post>
    <chapter>
    <chapter>
        ...
    </chapter>
    ...
</tale>
```

NOTE: When chpaters are present, it's not allowed to use global `begin` and `end` tags.

Normally, the order of tale's chapters is kept, unless it's explicitly changed, e.g.:

```xml
<tale>
    <chapter id="secondChapter">
        <pre>
            <after ref="firstChapter"/>
        </pre>
        ...
    </chapter>
    <chapter id="firtsChapter">
        ...
    <chapter>
    <chapter id="thirdChapter">
        ...
    </chapter>
</tale>
```

Chapters evaluation rules:
1. Chapters which aren't explicitly set to follow some other chapters, are evaluated in order of their appearance in the tale.
2. If there is a chapter which should follow a chapter that just ended, it's preferred.
3. Chapters aren't reevaluated.

It means that in the example above the order of the chapter is as the following: firstChapter, secondChapter, thirdChapter.

If chapters are not enough, then a tale can be divided into part:

```xml
<tale>
    <part>
        <pre>
            <!-- Prerequisites of the part. -->
        </pre>
        <chapter>
            ...
        </chapter>
        ...
        <chapter>
            ...
        </chapter>
        <post>
            <!-- Post state/changes of the part. -->
        </post>
    </part>
</tale>
```


