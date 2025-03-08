# godot4-camera3d-mouse-movement

```
extends Camera3D

# Mouse sensitivity (adjust as needed)
var mouse_sensitivity: float = 0.1

# Current vertical rotation in degrees (pitch)
var pitch: float = 0.0

func _ready():
	# Capture the mouse (hide and lock cursor)
	Input.set_mouse_mode(Input.MOUSE_MODE_CAPTURED)

func _input(event):
	if event is InputEventMouseMotion:
		# Rotate the parent (usually the CharacterBody3D) for horizontal movement (yaw)
		if get_parent():
			# Negative to invert the direction if needed
			get_parent().rotate_y(deg_to_rad(-event.relative.x * mouse_sensitivity))
		
		# Update the camera's vertical rotation (pitch)
		pitch -= event.relative.y * mouse_sensitivity
		# Clamp pitch to avoid flipping (e.g., between -80 and 80 degrees)
		pitch = clamp(pitch, -80, 80)
		rotation_degrees.x = pitch

```
