# react-native-settings-list
---
A clean and highly customizable React Native implementation of a list of settings for a settings page.<a name='top'/>
## Quick Access
* <a href='#install'>Installation</a>
* <a href='#usage'>Usage</a>
* <a href='#prop'>Prop values</a>
	* <a href='#sl'>\<SettingsList></a>
	* <a href='#slh'>\<SettingsList.Header></a>
	* <a href='#sli'>\<SettingsList.Item></a>
* <a href='#simple'>Simple Example</a>
* <a href='#realistic'>Realistic Example</a>


## <a name='install'>Installation</a>
---
Install the module with:


```
npm install react-native-settings-list --save
```
## <a name='usage'>Usage</a>
---
In your code, simply require/import the module:


```
import SettingsList from 'react-native-settings-list';
```

###### <a href='#top'>Top</a>

## <a name='prop'>Prop values</a>
---
### <a name='sl'>\<SettingsList></a>
The following props are used:

* **backgroundColor** : Used to set all Setting Items default background color (default color is white) (optional)
* **borderColor** : Sets border color for the settings list (optional)
* **defaultItemSize** : Used to set all the Setting Items default width (default is 50) (optional)

### <a name='slh'>\<SettingsList.Header></a>
The following props are used:

* **headerText** : (string) Text for the header (optional)
* **headerStyle** : (StyleSheet) Sets border color for the settings list (default color is black) (optional)

### <a name='sli'>\<SettingsList.Item></a>
The following props are used:

* **title** : (string) Text for the item (**required**)
* **titleStyle** : (StyleSheet) style for text (optional)
* **icon** : A component for the icon.  Doesn't need to be an image, accepts a node (optional)
* **itemWidth** : (number) Changes the individual item's width.  Overwrites **\<SettingsLists>** defaultItemSize (optional)
* **backgroundColor** : Changes the individual item's background color.  Overwrites default **\<SettingsList>** backgroundColor (optional)
* **onPress** : (func) On press Callback for item (optional)
* **hasNavArrow** : (true/false) Display the navigation arrow (optional)
* **arrowStyle** : (StyleSheet) Style for the navigation arrow (optional)
* **hasSwitch** : (true/false) Enable a switch component (optional)
* **switchState** : (true/false) Used to set the switch state (optional)
* **switchOnValueChange** : (func) On switches value change callback (optional)
* **titleInfo** : (string) Right side title information string (optional)
* **titleInfoStyle** : (StyleSheet) Style for title information string (optional)

###### <a href='#top'>Top</a>


## <a name='simple'>Simple Example</a>
---
Here is a simple example of the different things you can do with the module:


![Image of Simple Example](https://www.projectinf.com/content/images/github/simple.png =300x534)

The code behind it:

```
  constructor(){
    super();
    this.onValueChange = this.onValueChange.bind(this);
    this.state = {switchValue: false};
  }

  render() {
    return (
      <View style={{backgroundColor:'gray',flex:1}}>
        <View style={{flex:1, marginTop:50}}>
          <SettingsList>
          	<SettingsList.Header headerText='First Grouping' headerStyle={{color:'white'}}/>
            <SettingsList.Item
              icon={
                <View style={{height:30,marginLeft:10,alignSelf:'center'}}>
                  <Image style={{alignSelf:'center',height:40, width:40}} source={require('./about.png')}/>
                </View>
              }
              itemWidth={50}
              title='Icon Example'
              onPress={() => Alert.alert('Icon Example Pressed')}
            />
            <SettingsList.Item
              hasNavArrow={false}
              switchState={this.state.switchValue}
              switchOnValueChange={this.onValueChange}
              hasSwitch={true}
              title='Switch Example'/>
            <SettingsList.Item
              title='Different Colors Example'
              backgroundColor='#D1D1D1'
              titleStyle={{color:'blue'}}
              arrowStyle={{color:'blue'}}
              onPress={() => Alert.alert('Different Colors Example Pressed')}/>
            <SettingsList.Header headerText='Different Grouping' headerStyle={{color:'white', marginTop:50}}/>
            <SettingsList.Item titleInfo='Some Information' hasNavArrow={false} title='Information Example'/>
            <SettingsList.Item title='Settings 1'/>
            <SettingsList.Item title='Settings 2'/>
          </SettingsList>
        </View>
      </View>
    );
  }

  onValueChange(value){
    this.setState({switchValue: value});
  }
```

###### <a href='#top'>Top</a>

## <a name='realistic'>A more realistic example</a>

---
Here is an example that looks very very close to the default iPhone settings page.


![Image of Simple Example](https://www.projectinf.com/content/images/github/realistic.png =300x534)

The code behind this is:


```
  constructor(){
    super();
    this.onValueChange = this.onValueChange.bind(this);
    this.state = {switchValue: false};
  }

  render() {
    return (
      <View style={{backgroundColor:'#EFEFF4',flex:1}}>
        <View style={{borderBottomWidth:1, backgroundColor:'#f7f7f8',borderColor:'#c8c7cc'}}>
          <Text style={{alignSelf:'center',marginTop:30,marginBottom:10,fontWeight:'bold',fontSize:16}}>Settings</Text>
        </View>
        <View style={{backgroundColor:'#EFEFF4',flex:1}}>
          <SettingsList borderColor='#c8c7cc' defaultItemSize={50}>
            <SettingsList.Header headerStyle={{marginTop:15}}/>
            <SettingsList.Item
              icon={
                  <Image style={styles.imageStyle} source={require('./images/airplane.png')}/>
              }
              hasSwitch={true}
              switchState={this.state.switchValue}
              switchOnValueChange={this.onValueChange}
              hasNavArrow={false}
              title='Airplane Mode'
              titleStyle={{fontSize:16}}
            />
            <SettingsList.Item
              icon={<Image style={styles.imageStyle} source={require('./images/wifi.png')}/>}
              title='Wi-Fi'
              titleStyle={{fontSize:16}}
              titleInfo='Bill Wi The Science Fi'
              titleInfoStyle={styles.titleInfoStyle}
              onPress={() => Alert.alert('Route to Wifi Page')}
            />
            <SettingsList.Item
              icon={<Image style={styles.imageStyle} source={require('./images/blutooth.png')}/>}
              title='Blutooth'
              titleStyle={{fontSize:16}}
              titleInfo='Off'
              titleInfoStyle={styles.titleInfoStyle}
              onPress={() => Alert.alert('Route to Blutooth Page')}
            />
            <SettingsList.Item
              icon={<Image style={styles.imageStyle} source={require('./images/cellular.png')}/>}
              title='Cellular'
              titleStyle={{fontSize:16}}
              onPress={() => Alert.alert('Route To Cellular Page')}
            />
            <SettingsList.Item
              icon={<Image style={styles.imageStyle} source={require('./images/hotspot.png')}/>}
              title='Personal Hotspot'
              titleStyle={{fontSize:16}}
              titleInfo='Off'
              titleInfoStyle={styles.titleInfoStyle}
              onPress={() => Alert.alert('Route To Hotspot Page')}
            />
            <SettingsList.Header headerStyle={{marginTop:15}}/>
            <SettingsList.Item
              icon={<Image style={styles.imageStyle} source={require('./images/notifications.png')}/>}
              title='Notifications'
              titleStyle={{fontSize:16}}
              onPress={() => Alert.alert('Route To Notifications Page')}
            />
            <SettingsList.Item
              icon={<Image style={styles.imageStyle} source={require('./images/control.png')}/>}
              title='Control Center'
              titleStyle={{fontSize:16}}
              onPress={() => Alert.alert('Route To Control Center Page')}
            />
            <SettingsList.Item
              icon={<Image style={styles.imageStyle} source={require('./images/dnd.png')}/>}
              title='Do Not Disturb'
              titleStyle={{fontSize:16}}
              onPress={() => Alert.alert('Route To Do Not Disturb Page')}
            />
            <SettingsList.Header headerStyle={{marginTop:15}}/>
            <SettingsList.Item
              icon={<Image style={styles.imageStyle} source={require('./images/general.png')}/>}
              title='General'
              titleStyle={{fontSize:16}}
              onPress={() => Alert.alert('Route To General Page')}
            />
            <SettingsList.Item
              icon={<Image style={styles.imageStyle} source={require('./images/display.png')}/>}
              title='Display & Brightness'
              titleStyle={{fontSize:16}}
              onPress={() => Alert.alert('Route To Display Page')}
            />
          </SettingsList>
        </View>
      </View>
    );
  }

  onValueChange(value){
    this.setState({switchValue: value});
  }
```

###### <a href='#top'>Top</a>
