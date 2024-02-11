## What is an artifact?
- The files that contain both the compiled code and the resources that are used to compile them are known as artifacts. They are readily deploy-able files.
- In java an artifact would be a .jar, .war, ear file
- In NPM the artifact file would be a .tar.gz file
- In .NET the artifact file would be a .dll file

Source Code -> Build tool -> compilation -> Binary Code

Binary Code + Dependencies/ resources -> Artifact

## What is an artifact repository?
- An artifact repository is a repository which can store multiple different versions of artifacts. Each time the war file or tar.gz file is created it is stored in server dedicated for the artifacts.

Artifact version1/ version2/ version3 -> Artifact Repository => Deployment

## What is Nexus Repository?
- Nexus Repository is a tool used in DevOps methodology for multiple purposes. One of it's main purpose is to store artifacts(readily deploy-able code) that have been created in the code pipeline.
- Another one of it's purpose is to act as a sort of buffer for downloading dependencies for the build tools and languages.

Helps in downloading and managing dependencies

Build Tool ->(Asks for dependency) Nexus Repository Manager -> (Gets dependency from remote Repo) Remote Repository -> Nexus Repository Manager -> (Stores dependency in local repository) Local Server

## Features of Nexus
- Atlassian ==Crowd== Support
	- Nexus provides support for Atlassian Crowd which is a security software that is used to manage and track user accounts and application accesses.
	- It comes in-built with the Nexus Repository management pro and can be easily configured according to and organization's needs.
- Staging and Build Promotion
	- Nexus provides a staging feature that can easily be integrated with a organization's software development life-cycle.
	- It helps in staging all the release candidates(components of the software) that are tested meticulously before being isolated for release onto the production stage.
	- Since the feature allows for multiple candidates to be staged at the same time, then based on requirements the candidates can then be discarded or promoted.
- Tagging
	- Nexus provides the ability to tag components so they can be associated with each other. The usage of this feature is entirely up to the user as it has no specific use case, but it's mostly used in life-cycles to keep track of different builds or for differentiating between multiple projects during merges.
- User Token Support
	- Nexus uses a two-part token system to overcome the limited security of the build tools and removes the need to store sensitive information in text.
- High Availability
- Repository Health Check (RHC)
- Enterprise Support
- Group Blob Stores