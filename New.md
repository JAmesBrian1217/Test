<html>
	<head>
		<title>Day 1</title>
		<meta charset="utf-8">
		<link rel="stylesheet" type="text/css" href="../../css/main.css">
		<script src="../../js/react.min.js"></script>		
		<script src="../../js/react-dom.min.js"></script>
		<script src="../../js/browser.min.js"></script>
	</head>

	<body>
		<div id="container"></div>
		
		<script type="text/babel">
			
			var Comment = React.createClass({
				getInitialState: function () {
					return {editing: false}
				},
				edit: function ()
				{
					this.setState({editing: true});
				},
				remove: function ()
				{
					alert("Removing Comment");
				},
				save: function ()
				{
					var val = this.refs.newText.value;
					this.props.children = val;
					//~ console.log('New Comment : ' + val);
					this.setState({editing: false});
				},
				renderNormal: function ()
				{
					return (
						<div className="commentContainer">
							<div className="commentText">{this.props.children}</div>
							<button onClick={this.edit} className="button-primary">Edit</button>
							<button onClick={this.remove} className="button-danger">Remove</button>
						</div>
					);
				},
				renderForm: function ()
				{
					return (
						<div className="commentContainer">
							<textarea ref="newText" defaultValue={this.props.children} ></textarea>
							<button onClick={this.save} className="button-success">Save</button>
						</div>
					);
				},
				render: function () {
					if(this.state.editing)
					{
						return this.renderForm();
					}
					else
					{
						return this.renderNormal();
					}
				}
				
			});
			
			ReactDOM.render(<div className="board">
			<Comment> Hey my name is Mark </Comment>
			<Comment> Hey my name is JAmes </Comment>
			<Comment> Hey my name is Brian </Comment>
			</div>, document.getElementById("container"));
		</script>
	</body>
</html>

