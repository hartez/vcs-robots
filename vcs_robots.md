(This is a proposed standard. Please take a look at the [readme](https://github.com/hartez/vcs-robots/blob/master/readme.md) for more info)

# vcs-robots.txt

1. This file should be placed at the top level of the repository.
2. If this file isn't present, all robots should ignore the repository

# Format

The format of the file should be as follows:
	
    robot: [(robot-name) | *]
    [allow | deny]: [(folder) | (file) | *]
	
1. `(robot-name)` should be the commonly known name of the robot. If possible, this should be either a username (e.g., 'GunioRobot'), the name of the robot's source code repository (e.g., 'WhitespaceBot'), or a combination of both (e.g. 'GunioRobot/WhitespaceBot'). 
2. `*` after `robot:` indicates that this rule applies to all visiting robots.
3. `*` after `allow:` indicates that the entire repository can be visited by the specified robots. Otherwise, this rule only grants the robots access to the specified path. 
4. `*` after `deny:` indicates that the entire repository is off-limits to the specified robots. Otherwise, this rule only denies the robots access to the specified path. 
	
# Examples

## Allow any robot to access the entire repository:

	robot: *
	allow: *
	
## Allow a robot called 'RoboLinter' access only to the 'src/js' path:

	robot: RoboLinter
	allow: src/js

## Allow 'RoboLinter' only to 'src/js' and allow 'WhitespaceBot' access to the entire repo except for 'src/js':

	robot: RoboLinter
	allow: src/js

	robot: WhitespaceBot
	allow: *
	deny: 'src/js'

## Implementation

Robots implementing this standard are required to verify access to the repository before intitiating any of the following actions:

1. Creating a pull request
2. Submitting an issue
3. Commenting on an exisiting issue or pull request





