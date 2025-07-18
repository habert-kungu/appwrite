package main

import (
    "fmt"
    "github.com/appwrite/sdk-for-go/client"
    "github.com/appwrite/sdk-for-go/teams"
)

func main() {
    client := client.New(
        client.WithEndpoint("https://<REGION>.cloud.appwrite.io/v1") // Your API Endpoint
        client.WithProject("<YOUR_PROJECT_ID>") // Your project ID
        client.WithSession("") // The user session to authenticate with
    )

    service := teams.New(client)
    response, error := service.CreateMembership(
        "<TEAM_ID>",
        []interface{}{},
        teams.WithCreateMembershipEmail("email@example.com"),
        teams.WithCreateMembershipUserId("<USER_ID>"),
        teams.WithCreateMembershipPhone("+12065550100"),
        teams.WithCreateMembershipUrl("https://example.com"),
        teams.WithCreateMembershipName("<NAME>"),
    )

    if error != nil {
        panic(error)
    }

    fmt.Println(response)
}
