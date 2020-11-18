# alfred-translate Workflow (Researching)
Google translate for Alfer Workflow

*Note 1*: I am just looking for a new way to get translations done with Alfred since the last workflow stoped working. If you want to give a hand, please leave an issue.

*Note 2*: I have noticed when calling the request to the google api, they detected many submissions and they block for a moment my IP.

### Todo: 
- [ ] Get the correct query
- [ ] Multilanguage
- [ ] Pack it on an alfred workflow


# Documentation

- sl - source language code (auto for autodetection)
- tl - translation language
- q - source text / word
- ie - input encoding (a guess)
- oe - output encoding (a guess)
- dt - may be included more than once and specifies what to return in the reply.

Here are some values for dt. If the value is set, the following data will be returned:

- t - translation of source text
- at - alternate translations
- rm - transcription / transliteration of source and translated texts
- bd - dictionary, in case source text is one word (you get translations with articles, reverse translations, etc.)
- md - definitions of source text, if it's one word
- ss - synonyms of source text, if it's one word
- ex - examples
- rw - See also list.
- dj - Json response with names. (dj=1)

- client t probably represents the standalone google translate web app (as opposed to a mobile app, or the widget that pops up if you google search "translate")
- sl is source language
- tl is translate language (the language you want to translate into)
- srcrom seems to be present when the source text has no spelling suggestions

## Valid request
`https://translate.googleapis.com/translate_a/single?client=gtx&sl=en&tl=es&dt=t&q=house`

?client=gtx&sl="+ sourceLang + "&tl=" + targetLang + "&dt=t&q=" + encodeURI(sourceText)

[From stack overflow](https://stackoverflow.com/questions/57397073/difference-between-the-google-translate-api)

```https://translate.googleapis.com/translate_a/single?client=gtx&sl=en&tl=fr&dt=t&q=father&ie=UTF-8&oe=UTF-8```
returns this json:

```json
[
   [[ "père", "father", null, null,1]],
   null,
   "en"
]
```
While this `https://clients5.google.com/translate_a/t?client=dict-chrome-ex&sl=en&tl=fr&dt=t&q=father` returns this json:


```json
{
   "sentences":[
      {
         "trans":"père",
         "orig":"father",
         "backend":1
      },
      {
         "src_translit":"ˈfäT͟Hər"
      }
   ],
   "dict":[
      {
         "pos":"noun",
         "terms":[
            "père"
         ],
         "entry":[
            {
               "word":"père",
               "reverse_translation":[
                  "father",
                  "dad",
                  "parent",
                  "papa"
               ],
               "score":0.70910621,
               "previous_word":"le",
               "gender":1
            }
         ],
         "base_form":"father",
         "pos_enum":1
      },
      {
         "pos":"verb",
         "terms":[
            "engendrer",
            "concevoir"
         ],
         "entry":[
            {
               "word":"engendrer",
               "reverse_translation":[
                  "generate",
                  "engender",
                  "give rise to",
                  "beget",
                  "breed",
                  "father"
               ],
               "synset_id":[
                  52561
               ],
               "score":0.00017133754
            },
            {
               "word":"concevoir",
               "reverse_translation":[
                  "design",
                  "conceive",
                  "devise",
                  "plan",
                  "form",
                  "father"
               ],
               "synset_id":[
                  52561
               ],
               "score":4.8327973e-05
            }
         ],
         "base_form":"father",
         "pos_enum":2
      }
   ],
   "src":"en",
   "alternative_translations":[
      {
         "src_phrase":"father",
         "alternative":[
            {
               "word_postproc":"père",
               "score":1000,
               "has_preceding_space":true,
               "attach_to_next_token":false
            }
         ],
         "srcunicodeoffsets":[
            {
               "begin":0,
               "end":6
            }
         ],
         "raw_src_segment":"father",
         "start_pos":0,
         "end_pos":0
      }
   ],
   "confidence":1,
   "ld_result":{
      "srclangs":[
         "en"
      ],
      "srclangs_confidences":[
         1
      ],
      "extended_srclangs":[
         "en"
      ]
   },
   "query_inflections":[
      {
         "written_form":"father",
         "features":{
            "number":2
         }
      },
      {
         "written_form":"fathers",
         "features":{
            "number":1
         }
      }
   ],
   "target_inflections":[
      {
         "written_form":"père",
         "features":{
            "gender":1,
            "number":2
         }
      },
      {
         "written_form":"pères",
         "features":{
            "gender":1,
            "number":1
         }
      },
      {
         "written_form":"père",
         "features":{
            "number":2
         }
      },
      {
         "written_form":"pères",
         "features":{
            "number":1
         }
      }
   ]
}
```




## Language Name	Language Code
- Afrikaans	af
- Irish	ga
- Albanian	sq
- Italian	it
- Arabic	ar
- Japanese	ja
- Azerbaijani	az
- Kannada	kn
- Basque	eu
- Korean	ko
- Bengali	bn
- Latin	la
- Belarusian	be
- Latvian	lv
- Bulgarian	bg
- Lithuanian	lt
- Catalan	ca
- Macedonian	mk
- Chinese Simplified	zh-CN
- Malay	ms
- Chinese Traditional	zh-TW
- Maltese	mt
- Croatian	hr
- Norwegian	no
- Czech	cs
- Persian	fa
- Danish	da
- Polish	pl
- Dutch	nl
- Portuguese	pt
- English	en
- Romanian	ro
- Esperanto	eo
- Russian	ru
- Estonian	et
- Serbian	sr
- Filipino	tl
- Slovak	sk
- Finnish	fi
- Slovenian	sl
- French	fr
- Spanish	es
- Galician	gl
- Swahili	sw
- Georgian	ka
- Swedish	sv
- German	de
- Tamil	ta
- Greek	el
- Telugu	te
- Gujarati	gu
- Thai	th
- Haitian Creole	ht
- Turkish	tr
- Hebrew	iw
- Ukrainian	uk
- Hindi	hi
- Urdu	ur
- Hungarian	hu
- Vietnamese	vi
- Icelandic	is
- Welsh	cy
- Indonesian	id
- Yiddish	yi
