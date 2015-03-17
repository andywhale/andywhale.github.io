---
layout: post
title:  "Playing with Google Go"
date:   2015-03-17 18:30:00
categories: programming
thumbnail: http://golang.org/doc/gopher/frontpage.png

---

I finally found 20 minutes to have my first trial of the recent addition to Google's arsenal; Google Go. Having been working a lot with distances lately I decided to implement Haversine formula in Google Go, my next stop will hopefully be to tie this in with Google Maps API and trying to do something clever.

[Try the code in the go playground](https://play.golang.org/p/MZVh5bRWqN)

	package main

	import "fmt"
	import "math"

	const kmtomiles = float64(0.621371192)
	const earthRadius = float64(6371)

	func main() {
		var locationName [2]string
		var location [2][2]float64
		// York - lat,lon
		locationName[0] = "York"
		location[0][0] = 1.0803
		location[0][1] = 53.9583
		// Bristol - lat,lon
		locationName[1] = "Bristol"
		location[1][0] = 2.5833
		location[1][1] = 51.4500
		
		// Use haversine to get the resulting diatance between the two values
		var distance = Haversine(location[0][0], location[0][1], location[1][0], location[1][1])
		// We wish to use miles so will alter the resulting distance
		var distancemiles = distance * kmtomiles
		
		fmt.Printf("The distance between %s and %s is %.02f miles as the crow flies", locationName[0], locationName[1], distancemiles)
	}

	/*
	 * The haversine formula will calculate the spherical distance as the crow flies 
	 * between lat and lon for two given points in km
	 */
	func Haversine(lonFrom float64, latFrom float64, lonTo float64, latTo float64) (distance float64) {
		var deltaLat = (latTo - latFrom) * (math.Pi / 180)
		var deltaLon = (lonTo - lonFrom) * (math.Pi / 180)
		
		var a = math.Sin(deltaLat / 2) * math.Sin(deltaLat / 2) + 
			math.Cos(latFrom * (math.Pi / 180)) * math.Cos(latTo * (math.Pi / 180)) *
			math.Sin(deltaLon / 2) * math.Sin(deltaLon / 2)
		var c = 2 * math.Atan2(math.Sqrt(a),math.Sqrt(1-a))
		
		distance = earthRadius * c
		
		return
	}
	
A site I found really useful, and well worth checking out is [go by example](https://gobyexample.com).