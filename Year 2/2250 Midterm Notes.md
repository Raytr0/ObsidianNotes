Strongly typed language (data holder is specific and can only hold that type unlike java auto conversion)
Explicitly typed: bool varName, byte varName ect
Implicitly typed: use var infront of variable name

CharacterController controller;
Vector3 movePos;
float speed = 3;
private void OnCollisionEnter(Collision collision){
	collision.gameObject.name;
}

void Update(){
	movePos.x = Input.GetAxis("Horizontal") * speed;
	movePos.z = Input.GetAxis("Vertical") * speed;
controller.Move(movePos)
}