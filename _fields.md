# Fields Documentation

This document provides detailed description of various fields used in our application. Fields are the specific data elements you can request about an object.

---

## Fields List

## 1. **_id**

- **Description**: This is the unique identifier of the field.
- **Datatype**: `String`
- **Usage**: Used as a primary key in the database.

```bash
_id

```


## 2. **Label**

- **Description**: This is the field label that need to be display on UI.
- **Datatype**: `String`
- **Usage**: By what name you want to visualize this field. (For example - Device name)

```bash
label
```

## 3. **Key**

- **Description**: This is the field key that will be unique across database.
- **Datatype**: `String`
- **Usage**: For example - dName

```bash
key
```

## 4. **ValueType**

- **Description**: This is the field type like number string or boolean.
- **Datatype**: `Integer`
- **Usage**: It is to validate the datatype of value.

```bash
valueType
```

## 5. **ValueOption**

- **Description**: This is the list of options for dropdown.
- **Datatype**: `Array`
- **Usage**: (For exapmple: [{key:1,label:"Today"},{key:2,label:"Yestarday"}])

```bash
valueOption
```

## 6. **Create**

- **Description**: `create` - Field should be saved/stored or not
`canStore` should define that the data should be stored or not and also find out whether the field is UI based or backend based. `condition` to make it true or not.
- **Datatype**: canStore - `Boolean` , condition - `expression/js function`
- **Usage**: This is in case of initializing new fields.

```bash
create: {
   canStore 
   condition : {
        dependentField: [],
        expr:
   }
}
```

## 7. **Edit**

- **Description**: `edit` - defined field is editable or not.
`isEditable` - It should define field is editable or not.
`condition` - We can make editable conditionally with the help of this function.
- **Datatype**: isEditable - `Boolean` , condition - `expression/js function`
- **Usage**: To adjust field properties or configurations.

```bash
edit:{
   isEditable
   condition:{
         dependentField:[],
         expr:
   }
}
```


## 8. **Visible**

- **Description**: `visible` - defined field is visible on ui or not.
`isVisible` - It should define field is visible or not.
`condition` -  We can make visible conditionally with the help of this function.
- **Datatype**: isEditable - `Boolean` , condition - `expression/js function`
- **Usage**: To control field visibility based on user roles.

```bash
visible:{
     isVisible
     condition:{
           dependentField:[],
           expr:
    }
}
```


## 9. **Update**

- **Description**: update - In the case when we want to update a field. 
`updateSource` -  update to database or device
`sendToDevice` - field value should be sent to device or not
`conditionalSend` - action on one field and another field data should send

- **Datatype**: updateSource - `Integer[Enum]` , sendToDevice - `Boolean`, keys - `Array of strings`, value - `expression/js function`
- **Usage**: To modify existing field values.

```bash
update:{
    updateSource
    sendToDevice
    condition:{
         dependentField: []
         expr: 
      }
}
```


## 10. **onDelete**

- **Description**: `onDelete` - What should happen after delete action
`type` - Enum for action that should happen on deleting 
`value` - some value which should save data on deleted field
- **Datatype**: type - `Integer[Enum]` , value - `string/integer`
- **Usage**: To Remove unwanted fields from records.

```bash
onDelete:{
   type
   value
}
```


## 11. **Parsing**

- **Description**: `parsing` - parsing or manipulation of value
`ui2db` - parsing from ui to db 
`dependentField` - This field's parsing is depenedent to other field's value.
`parsing` - function to manipulate data.
`db2ui` - parsing from database to ui.
`device2db` - prasing from device to db.
`datatype` - It defines what will be datatype for storing data in database, it will be required when parsing 
- **Datatype**: isEditable - `Boolean` , condition - `expression/js function`
- **Usage**: For transforming data from one format to another, making it more readable and understandable. 

```bash
edit:{
   isEditable
   condition:{
         dependentField:[],
         expr:
   }
}
```


## 12. **Validation**

- **Description**: `validation` - if any kind of validation is required for that field
`validationType` - Which type of validation like required,unique etc.
`dependentField` - any other field value is required for this field validation.
`function` - giving condition to validate in expression format.
`query` - query required for validation of field.
- **Datatype**: validationType - `String` , dependentField - `Array of strings`, function - `js function`, query - `expression format`
- **Usage**: To enforce data integrity rules for fields.

```bash
validation:[
{
    validationType:
    dependentField:[]
    function:
    query:
}
]
```

>EXAMPLE
>
> Here is an example of ...



## 13. **Expression**

- **Description**: `expr` - Query for getting the field value
`user` - Query for the field which will provided by the user
`default` - base level query which will always runs by default to get the field value
- **Datatype**: 
- **Usage**: 

```bash
expr:{
     user:
     default:
}
```


## 14. **Real Time Update**

- **Description**: This decides whether the field will be forwarded on socket or not.
- **Datatype**: `Boolean` 
- **Usage**: Instantly refreshing data to reflect current information.

```bash
realTimeUpdate
```


## 15. **Read**

- **Description**: This is in the case where the field will fetch data from database or hardware.
- **Datatype**: `Integer`
- **Usage**: 

```bash
read:{
    getSource
    condition:{
         dependentField: []
         expr: 
      }
}
```

## 16. **Type**

- **Description**: It is the type of the field.
- **Datatype**: `Integer`
- **Usage**: 

```bash
type
```

## 17. **Copy Value**

- **Description**: This is case where on clone/copy whether this field should be copied or not.
- **Datatype**: `Boolean`
- **Usage**: 

```bash
copyValue
```

## 18. **Help**

- **Description**: To show on the UI hovering the field.    
- **Datatype**: `String`
- **Usage**: In case of help.

```bash
help
```

## 19. **Type ID**

- **Description**: It is the typeID of the field.
- **Datatype**: `Integer`
- **Usage**: 

```bash
typeId
```

## 20. **Relation**

- **Description**: `relation` - where and how relation is established
`source` - collection name from where relation is established
`key` - which field is related
`localKey` -key by which it is stored in the current document
- **Datatype**: source, key, localKey -`String`
- **Usage**: In the case where the realtion has to be established.

```bash
relation:{
    source
    queryKey
    projectionKey
    localKey
}
```

## 21. **DB Config**

- **Description**: `dbConfig` - database configuration like where to save or from where to get data
`dbType` - Which type of database this field is related like mongodb or influxdb
`index` - This is indexed field or not. 
- **Datatype**: dbType - `Integer[Enum]`, source-`String`, index - `Boolean`
- **Usage**: This is to know the database configuration as in where to store/get data.

```bash
dbConfig:{
     dbType
     source,
     index
     primaryKey
}
```

## 22. **Org ID**

- **Description**: This is the unique id of an organization.
`index` - This is indexed field or not. 
- **Datatype**: `String`
- **Usage**: 

```bash
orgs_id:
```

## 23. **Group**

- **Description**: This is for grouping fields.
- **Datatype**: `Array of strings`
- **Usage**: 

```bash
group
```

## 24. **System Field**

- **Description**: This field is system generated field or added by user.
- **Datatype**: `Boolean`
- **Usage**: 

```bash
systemField
```

## 25. **Place Holder**

- **Description**: This is for the input fields.
- **Datatype**: `String`
- **Usage**: 

```bash
placeHolder
```

## 26. **Log Changes**

- **Description**: This is to store logs of every action or not.
- **Datatype**: `Boolean`
- **Usage**: 

```bash
logChanges
```

## 27. **Created By**

- **Description**: This defines who created the field.
- **Datatype**: `String`
- **Usage**: 

```bash
createdBy
```

## 28. **Created At**

- **Description**: This defines when the field was created.
- **Datatype**: `String`
- **Usage**: 

```bash
createdAt
```

## 29. **MOdified By**

- **Description**: This defines who edited the field last.
- **Datatype**: `String(userId)`
- **Usage**: 

```bash
modifiedBy
```

## 30. **State**

- **Description**: This describes the state of the field i,e. active/archived/deleted data.
- **Datatype**: `Integer[Enum]`
- **Usage**: 

```bash
state
```

## 31. **Access control**

- **Description**: This is in case when access has to be given.
- **Datatype**: `Boolean`
- **Usage**: This field will be defined if RBAC is required or not. Only fields which has only true value will be shown in Role CRUD.

```bash
accessControl
```


## 32. **Access**

- **Description**: This defines what type of access is to be given to which role.
- **Datatype**: view,control - `Array<string>`
- **Usage**: 

```bash
access : {
       view : 
       control : 
}
```

## 33. **Default**

- **Description**: It gives us default value and also handles user increment field with this.
- **Datatype**: view,control - `Array<string>`
- **Usage**: 

```bash
default: {
    value,
    expr,
    seq
}
```

## 34. **Parent ID**

- **Description**: It is used for handling the condition in which user want to view RPhase voltage , YPhase voltage and voltage in same column.
- **Datatype**:
- **Usage**: 

```bash
parentID
```


## 35. **Value**

- **Description**: It is used to store the value of the field.(Currently used for filter type of fields).
- **Datatype**:
- **Usage**: 

```bash
value
```


## 36. **Dependent**

- **Description**: It is used for modifying field properties like label or parsing of any other field like we have to view different label for temp field in different device page.
- **Datatype**:
- **Usage**: 

```bash
dependent
```


















