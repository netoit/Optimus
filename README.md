# Optimus
Optimus Repository is the default configuration that my own Raspberry Pi 3 B will run. More info on my own blog.

# History
My idea is to create a "Test-server" with following purpose>
	Main Docker (Only Host will access to admin it). Contains>
		LAMP+Python => Web API using Python to UP Containers and give access to another users to use their Dockers

	User's Dockers>
		Each user will gestione their own dockers, without have admin access to other dockers.

Then this scenario is to create a "Host-server" but instead to give an IP to manage their server, will use the same IP but different port to each service that the user want UP.
