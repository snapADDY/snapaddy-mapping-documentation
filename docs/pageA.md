1. Mapping Examples

    // Example address object:
    {
      firstName : 'Giuseppe', 
      lastName : 'Spampinato', 
      gender : 0, 
      social: { 
        xing: { 
          url: 'www.xing.com'
        }
      } 
    }

Name

Mapping

Ergebnis

direct replacement

{{firstName}}

'Giuseppe'

deep properties

{{social.xing}}

'www.xing.com'

with default value

{{fullName || firstName}}

'Giuseppe'

hardCoded default value

{{fullName || 'Klaus'}}

'Klaus'

2. Specials

2.1 Or

The || -Operator can be used to cover several cases. Could the first value not be found, the second one will be mapped. If it's also not available, the third one and so on (see table)

2.2 null

In the mapping a value can be set ({{null}}) directly or via{{ fullName || null}}conditionally.

2.3 _delete

The _delete-Operator ignores a property in the mapping if the value that should be mapped is not found.

    // Example adress object:
    {
      firstName : 'Giuseppe', 
      lastName : 'Spampinato', 
      gender : 0, 
      social: { 
        xing: { 
          url: 'www.xing.com' 
      } 
    }

    // Example mapping:
    {
      fullname : '{{firstName}} {{lastName}}', 
      id : '{{ person_id || _delete }}'
    }

    // Example output:
    {
      fullname : 'Giuseppe Spampinato'
    }

2.4 Ternary-Operator

The Ternary-Operator (also ?-Operator) works like a if in programming.

Structure<Condition>? (<mapping if true>) : (<mapping if false>)Example'{{ gender == -1? ('') : (gender == 0? ('Herr') : ('Frau')) }}'
