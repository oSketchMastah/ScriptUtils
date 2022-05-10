# ScriptUtils

Make MISetupUtils executable and execute to install all the utilities

-Typical workflow:

	-Setup work with GitInit using all four parameters (personal and shared branch)
	
	-call GitInit with no parameters in work directory occassionally to get updates
	
	-call GitSend from working directory to send in your work to be reviewed/processed/merged
	
******************************************************************

GitInit: (Owner Repo) (NewBranch) (BranchName) -> effects

	With no args, pulls code from remote if .git subdirectory is present or assumes you would like to create a new shared repository out of the current directory, otherwise clones a remote repo specified by owner and repo name, optionally taking a name for created branch, and the branch to be cloned

Ex. "GitInit MainIntelligence MIUtil" : Get MainIntelligence MIUtil repo (w/ all branch information)

    "GitInit MainIntelligence MIUtil dev" : 
    	Get and track only master branch of MainIntelligence MIUtil repo, make a "dev" branch

    "GitInit MainIntelligence MIUtil $(git config --get user.name) dev" : 
    	Get and track "dev" branch of MainIntelligence MIUtil repo, creating a new branch w/ our github name

******************************************************************

GitListRepos: user_entity -> newline seperated list of repo names

	Gives you (no whitespace containing) names of repos belonging to a user/organization

Ex. "GitListRepos MainIntelligence | while read repo; do GitInit MainIntelligence $repo; done"

	Clone all the repos belonging to MainIntelligence

******************************************************************

GitSend: commit_message -> effects on remote

     Used in repo directory, adds all your changes to be committed, commits them (with the message), and pushes to remote

******************************************************************

GitExtend: Owner Repo NewBranch (branchname)

	Creates a new remote branch, unchanged from the specified branch (or master, if unspecified)

Ex. "GitExtend MainIntelligence MIUtil Dev": Make a 

******************************************************************

GitSetup: (email) -> effects

	Can specify an email, or it will interactively ask for your email if it is needed,
	Sets up an SSH agent for interacting with remote repos, guiding you through setup if necessary

******************************************************************

Binstall: executables... -> effects

	Installs binaries for use in any scope, setting up executable permission.

******************************************************************

GitAllRepos: Owner -> effects

	Downloads all the git repositories of the owner (a git user or organization)

******************************************************************

GitUpdate: void -> effects

	Use a "gitcfg" file in current directory (of newline seperated paths) to specify
		directories in which to pull (and recieve updates from remote)

******************************************************************

