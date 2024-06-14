# DevOps-Course
#!/bin/bash
# Github api url
API_URL= "https://api.github.com"
# GitHub username and access token
USERNAME=$username
TOKEN=$token
# user and repository information
REPO_OWNER=$1
REPO_NAME=$2
# Function to make a GET request to the Github API
function github_api_get {
  local endpoint="$1"
  local url="${API_URL}/${endpoint}"
  #sent a GET request to Github API with authentication
  curl -s -u "${USERNAME}:${TOKEN}" "url"
}
# function list userswith read access to the repository
function list_users_with_read_access{
 local endpoint= "repos/${REPO_OWNER}/${REPO_NAME}/collaborators"
 #fetch the list of collaborators on repo
 collaborators="$github_api_get"$endpoint"|jq -r '.[]|select(.permissions.pull=true)|.login')"
 #display the list aof collaborators with read access
 if [[-z "$collabarators"]]; then 
   echo "no users with read access gor ${REPO_OWNER}/${REPO_NAME}."
 else
   echo "users with read access to ${REPO_OWNER}|{REPO_NAME}:"
   
   echo "collaborators"
 fi
}
# main script 
 echo "listing users with read access to ${REPO_OWNER}/${REPO_NAME}..."

 
