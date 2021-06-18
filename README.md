
# LwM2M Registry
This public repository is dedicated to store and register new LwM2M Objects and Reusable Resources.
  
# Registration Process  

![image](https://user-images.githubusercontent.com/3258579/49321895-7e517a80-f4bf-11e8-9337-9ff1fd027432.png)

## 1. Issue created by the Submitter
* Create an **[Issue](https://github.com/OpenMobileAlliance/lwm2m-registry)** before registering your ```Objects``` or ```Reusable Resources```
* In the Issue indicate what you would like to do:
  1. Create Version 1.0 of a new Object
  2. Create a new Version X.Y of an existing Object
  3. Create one or more Reusable Resources

## 2. New branch created by the Maintainer
* Based on the information provided the Maintainer will:
  * Create a new `topic` or `feature-branch` to apply the changes
    * **Branch Name**: `ObjID_companyName`
  * Reserve one or more Objects ID or/and Reusable Resources ID based on the Issue

## 3. New or revised Object created by the Submitter
* You can create the new Object using the **[LwM2M Editor](http://devtoolkit.openmobilealliance.org/OEditor/Legal?back=default.aspx)** 
  * **[Guidelines](https://github.com/OpenMobileAlliance/lwm2m-registry/wiki/Guidelines)** & **[Best Practice](https://wiki.openmobilealliance.org/display/TOOL/LwM2M+Best+Practice)**

## 4. Pull Request created by the Submitter
* The Submitter must create a Pull Request against the allocated branch
* Please follow these steps carefully:

### 4.1 Update the `DDF.xml` file
    * If the submission contains a new Object the `DDF.xml` file must be updated
    * The `DDF.xml` file contains all the Objects in the Registry. Therefore, each time that a new Object is added  the `DDF.xml` file must be updated with a new Object placeholder.
    
```xml
   Example of an Object placeholder for Object ID = 0, version 1.0

    <Item>        
        <ObjectID>0</ObjectID>
        <!-- Integer, this number is allocated by the Maintainer -->
        <!-- ObjecID also called ObjID-->
      
        <URN>urn:oma:lwm2m:oma:0</URN>
        <!-- URN of the object 
             for other versions than v1.0 the URN mus include the version, e.g., for v1.1 the URN is urn:oma:lwm2m:oma:0:1.1 -->
        <Name>LWM2M Security</Name>
        <!-- Name of the object -->
      
        <Description>Object description</Description>
        <!-- Description of the Object -->
      
        <Owner>Test WG</Owner>
        <!-- Name of the organization that has registered the object -->
      
        <Source>0</Source>
        <!-- Type of Object: 
             0 = defined by OMA, 
             1 = defined by external Standards Development Organizations, 
             2 = private or individual -->
      
        <Ver>1.0</Ver>
        <!-- Version of the object -->
      
        <DDF>version_history/0-1_0.xml</DDF>
        <!-- URL to the xml file describing the object 
         latest version the filename is stored in the root as ObjID.xml
         Previous versions the filea are stored in the version_history folder as ObjID-X_Y.xml, were X.Y is the Object Version.-->
      
        <Vorto></Vorto>
        <!-- VOID- Link that opens the Object in the Vorto environment -->
      
        <DDFLink>1</DDFLink>
        <!-- 0 => if link to object should not be visible, 
             1 => if object should be visible (default) -->
      
        <TS>http://www.openmobilealliance.org/release/LightweightM2M/V1_0_2-20180209-A/OMA-TS-LightweightM2M-V1_0_2-20180209-A.pdf</TS>
        <!-- URL to the TS of the object, not visible, not used -->
        
        <TSLink>1</TSLink>
        <!-- 0 => if link to TS should not be visible, 1 => if link to TS should be visible (default) -->
    </Item>
 ```
 
### 4.2 Update or create a new `ObjID.xml` file
    * In this step, if you are creating:
      * A first version of an Object, version 1.0, then you must upload a fully qualified `ObjID.xml` file to the allocated branch
      * A revision of an existing Object, e.g. version 1.1 of Object ID `0.xml`, then you can modify directly the existing Object in the root of the allocated branch but you will have to add the new revision of the Object to the `history_folder`, see next step.
    
### 4.3 Add a new `ObjID-X_Y.xml` file to the `version_history` folder
    * Each Object version, must have a file in the `version_history` folder
    * The name of the file is e.g., for Object ID 0, Version 1.1, the filename is `0-1_1.xml`
      * The content of the `0-1_1.xml` is the content as the Object file `0.xml` for version 1.1

### 4.4 Updates the `Common.xml` file (if adding new Reusable Resources)**
    * If the request is to add one or more Reusable Resources, then for each Reusable Resource a new placeholder must be added to the `Common.xml` file

  ```xml
    Example of Reusable Resource placeholder
          
      <Item ID="4000">
        <!-- Resource ID of the reusable resource 
             Reusable Resource IDs are allocated by the Maintainer, this is one of the reasons to raise an Issue in the first place -->
        
        <Name>ObjectInstanceHandle</Name>
        <!-- Name of the reusable resource -->
        
        <Operations>R</Operations>
        <!-- Allowed Operation on the reusable resource-->
        
        <Type>Objlnk</Type>
        <!-- Type of the reusable resource -->
        
        <RangeEnumeration></RangeEnumeration>
        <!-- Range/Enumeration of the reusable resource
             A range is expressed with (..),e.g., from 0 to 10, it is expressed as; `(0..10)`
          -->
        
        <Units></Units>
        <!-- Unit of the reusable resource 
             Please note the units expressed in this element MUST comply with the units defined in the SenML Registry -->
        
        <Submitter>OMA</Submitter>
        <!-- Name of the organization that has registered the object -->
        
        <Description><![CDATA[Reusable Resource Description]]></Description>
        <!-- Description of the reusable resource -->
        
        <TS></TS>
        <!-- Link to the technical specification (word, pdf etc.) -->
        
        <TSLink>0</TSLink>
        <!--    0 => if link to TS should not be visible, 1 => if link to TS should be visible (default) -->
      </Item>
  ```
  

   
4. To create successful ```Object(s)``` | ```Reusable Resource(s)``` use the provided **[LwM2M Editor](http://devtoolkit.openmobilealliance.org/OEditor/Legal?back=default.aspx)** and follow the .   
   
5. Submit your ```Pull Request(s),(PRs)```, containing your ```Object(s)``` | ```Reusable Resource(s)``` registrations against the allocated branch - See **[Object PR submission guidelines](https://wiki.openmobilealliance.org/display/TOOL/Pull+Request+Object+submission)**.
    > Note: The OMA staff will [close]() any ```PR(s)``` submitted against the incorrect branch. 
  
6. Participate in the feedback provided by the Technical Working Group. The Group will provide comments to help you to improve your registration.   
  
7. Once your submission has been accepted it will be incorporated into the *["master"](https://github.com/OpenMobileAlliance/lwm2m-registry/tree/master)* branch and published in the repository.
