import React from "react";

export class Main extends React.Component {
    render() {
        return (
            <div>
                <div className="row">
                    <div className="col-xs-12">
                        <h1>The Main Page</h1>
                    </div>
                </div>
                <div className="row">
                    <div className="col-xs-12">
                        <button
                            className="btn btn-primary"
                            onClick={() => this.props.changeUsername('Anna')}>Change the Username</button>
                    </div>
                </div>
            </div>
        );
    }
}






import React from "react";

export class User extends React.Component {
    render() {
        return (
            <div>
                <div className="row">
                    <div className="col-xs-12">
                        <h1>The User Page</h1>
                    </div>
                </div>
                <div className="row">
                    <div className="col-xs-12">
                        <p>User Name: {this.props.username}</p>
                    </div>
                </div>
            </div>
        );
    }
}





import React from 'react';
import connect from 'react-redux'; //include a connect fct to connect react with redux

import { User } from './User';
import { Main } from './Main';


export class App extends React.Component {
    
    render() {
        return (
            <div>
                <Main changeUserName={()=>this.props.setName('lsidem')} />
                <User username="siemah" />
            </div>
        );
    }
}

//conert a global var which mean a state from store 
//to a local var which is a props into App component
const mapStateToProps = (state) => {
    return {
        user: state.userReducer,
        math: state.mathReducer
    }
}

//dispatch a state and action
const mapDispatchToProps = (dispatch) => {
    return {
        setName: (name) => {
            dispatch({
                type: 'SET_NAME',
                payload: name
            });
        }
    }
}

//connect a react with redux and pass a 2 fun as args and this return fun
//which is expect a component as args

connect(mapStateToProps, mapDispatchToProps)(App);
