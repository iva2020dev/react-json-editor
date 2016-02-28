# react-json-editor
JSON editor for React

# Install 
[![NPM](https://nodei.co/npm/react-json-edit.png)](https://npmjs.org/package/react-json-edit)

# How to use

* import JsonEditor component

`import { JsonEditor } from 'react-json-edit';`

* Add to render method and supply a callback method


```javascript
class MyComponent extends Component {

  constructor(props) {
    super(props);
    this.state = {
      json: undefined /*  setup here or load elsewhere */
    }
  }
  
  callback = (changes) => {
    this.setState({json: changes.json});
  };

  render() {
    return (
      <div>
        <JsonEditor json={this.state.json} propagateChanges={this.callback}/>
      </div>
    );
  }
}
```

# Parse
It possible to parse and see errorMessage from parsing with the following helper method

```javascript
import { parse } from 'react-json-edit';

load_callback(text) {
   const parsed = parse(text);

   if(parsed.json === undefined) {
       this.setState({message: parsed.errorText});
   } else {
       this.setState({json: parsed.json, message: undefined});
   }
}

render() {
  return (
   <div>
     <JsonEditor json={this.state.json} propagateChanges={this.callback}/>
     <span>{this.state.message}</span>
   </div>
  );
}
```

# TODO
1. Style:
  - loading CSS
  - Isomorphic rendering of CSS
  - More different styles
  - Custom layout
2. Test!
3. More setup options
  - Number of levels
  - Configure add buttons
  - Schema for adding stuff
4. Eventually built in text editor where result is parsed automatically