```
//将军借兵
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>

    <script crossorigin src="https://unpkg.com/react@16/umd/react.production.min.js"></script>
    <script crossorigin src="https://unpkg.com/react-dom@16/umd/react-dom.production.min.js"></script>
    <script crossorigin src="https://npmcdn.com/babel-core@5.8.38/browser.min.js"></script>
</head>
<body>
    <div id="root"></div>
    <script type="text/babel">
        class King extends React.Component{
        constructor(props) {
        super(props);
        this.state={
            solider:100
        }
        // this.add = this.add.bind(this)
        this.change = this.change.bind(this);
      }
      change(){
        this.setState({
          solider:this.state.solider-10 
        })
      }
      
      render(){
        return(
            <div>
                <p>国王的兵数：{this.state.solider}</p>
                <General askF={this.change} solider={100}></General>
            </div>

        )
      }
    }
    class General extends React.Component{
      constructor(props) {
        super(props);
        this.state={
            solider:this.props.solider
        }
        this.ask = this.ask.bind(this);
      }
      ask(){
        this.setState({
          solider:this.state.solider+10
        })
        this.props.askF();
      }
      render(){
        return(
          <div>
            {this.props.children}
            <p>将军兵数：{this.state.solider}</p>
            <button onClick={this.ask}>调兵</button>
          </div>
          
        )
      }
    }
    ReactDOM.render(
      <King/>,
      document.getElementById('root')
    )
  </script>
</body>
</html>
```
