# Robux Stream Donations - Web Source for OBS

A simple server that displays Roblox donations in a Streamlabs-like way to an OBS web

## Why

I recently got permanently suspended from PayPal. As I got that e-mail I thought "Man, isn't there a way to do the same but with Roblo Robux? It seems easy enough." But, after looking around for a while, I haven't found any resource that allows you, as a streamer, to easily send HTTP requests to a web server for them to display on OBS.

This resource allows you to open your own local webserver and have a game send donation data to it.

## What?

Rest API hosted on "http://localhost:3000/api/donations" using ExpressJS.

## How?

Use NPM and install ExpressJS. The rest is already taken care for you?

## How do I send requests on Roblox?

You can use Roblox's HTTP Service. Here's a code example.

```
local MarketplaceService = game:GetService("MarketplaceService")
local HttpService = game:GetService("HttpService")

function sendDonation(donorName, amount)
	local url = "http://localhost:3000/api/donations"
	local data = {
		donorName = donorName,
		amount = amount
	}
	local jsonData = HttpService:JSONEncode(data)

	HttpService:PostAsync(url, jsonData, Enum.HttpContentType.ApplicationJson)
end

```