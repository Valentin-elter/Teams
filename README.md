# Teams
A second-year student project, a server that manages a collaborative communication application similar to Microsoft Teams®.

## Features

The application is a service that manages multiple communication teams, where discussions are organized as follows:
* threads (initial post and additional comments) within a specific channel
* Personal discussions

The application allows for the following actions:
* Creating, joining, and leaving teams
* Creating users
* Creating channels within a team
* Creating threads within a channel
* Creating comments within a thread
* Saving and restoring users, teams, channels, threads, and associated comments
* Personal discussions (between users)
* Saving and restoring personal discussions

### Client

The client will handle the following commands from standard input:
* __/help :__ show help
* __/login [“user_name”] :__ set the user_name used by client
* __/logout :__ disconnect the client from the server
* __/users :__ get the list of all users that exist on the domain
* __/user [“user_uuid”] :__ get information about a user
* __/send [“user_uuid”] [“message_body”] :__ send a message to a user
* __/messages [“user_uuid”] :__ list all messages exchange with an user
* __/subscribe [“team_uuid”] :__ subscribe to the event of a team and its sub directories (enable reception of all events from a team)
* __/subscribed ?[“team_uuid”] :__ list all subscribed teams or list all users subscribed to a team
* __/unsubscribe [“team_uuid”] :__ unsubscribe from a team
* __/use ?[“team_uuid”] ?[“channel_uuid”] ?[“thread_uuid”] :__ specify a context team/channel/thread
* __/create :__ create a subresource based on the current context
* __/list :__ list all subresources based on the current context
* __/info :__ display information about the current context

#### /CREATE

When the context is not defined (/use):
* __/create [“team_name”] [“team_description”] :__ create a new team
When team_uuid is defined (/use “team_uuid”):
* __/create [“channel_name”] [“channel_description”] :__ create a new channel
When team_uuid and channel_uuid are defined (/use “team_uuid” “channel_uuid”):
* __/create [“thread_title”] [“thread_message”] :__ create a new thread
When team_uuid, channel_uuid and thread_uuid are defined (/use “team_uuid” “channel_uuid” “thread_uuid”):
* __/create [“comment_body”] :__ create a new reply

#### /LIST
When the context is not defined (/use):
* __/list :__ list all existing teams
When team_uuid is defined (/use “team_uuid”):
* __/list :__ list all existing channels
When team_uuid and channel_uuid are defined (/use “team_uuid” “channel_uuid”):
* __/list :__ list all existing threads
When team_uuid, channel_uuid and thread_uuid are defined (/use “team_uuid” “channel_uuid” “thread_uuid”):
* __/list :__ list all existing replies

#### /INFO
When the context is not defined (/use):
* __/info :__ display currently logged user infos
When team_uuid is defined (/use “team_uuid”):
* __/info :__ display currently selected team infos
When team_uuid and channel_uuid are defined (/use “team_uuid” “channel_uuid”):
* __/info :__ display currently selected channel infos
When team_uuid, channel_uuid and thread_uuid are defined (/use “team_uuid” “channel_uuid” “thread_uuid”):
* __/info :__ display currently selected thread infos

#### GENERAL INFORMATIONS
Please note that all arguments of the existing commands should be quoted with double quotes.
A missing quote should be interpreted as an error.
Please note that all the names, descriptions and message bodies have a pre-defined length which will be
as follow:
* MAX_NAME_LENGTH 32
* MAX_DESCRIPTION_LENGTH 255
* MAX_BODY_LENGTH 512

## Build on Linux (Ubuntu)

### 1. Set environement variable (for each terminal):

	export LD_LIBRARY_PATH=/Path/to/folder/Teams/libs/myteams

### 2. Build teams from my repo:
	make
	./myteams_server [PORT] (ex: 4000)
    ./myteams_cli [I.P.] [Port used by server] (ex: 127.0.0.1 4000)

## Screenshots

![Alt text](screenshots/1.png?raw=true "1")
![Alt text](screenshots/2.png?raw=true "2")