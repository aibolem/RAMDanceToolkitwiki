# Recognizer


### Summary

This page describes a number of recognizers used in RAMDanceToolkit.

### Table of Contents

- [Introduction to ramBaseRecognizer](Introduction to ramBaseRecognizer)
- [ramGeometry](ramGeometry)
- [ramMovementAnalyser](ramMovementAnalyser)
- [ramTimerdMovementAnalyser](ramTimerdMovementAnalyser)
- [ramBalancer](ramBalancer)


# Introduction to ramBaseRecognizer

In RAMDanceToolkit 1.0.0, ramBaseRecognizer is an experimental class. There are many kinds of analysis results that might be returned. Because of this, ramBaseRecognizer doesn't have a uniform format. If you have any issues with this class, plesae create a new issue or send a pull request! ramBaseRecognizer is still a work in progress :)


The Current ramBaseRecognizer implementation is empty:

	class ramBaseRecognizer : public ramUnit {
	public:
	};

For an examlple of how to use a recognizer, please look at the [Notation scene](https://github.com/YCAMInterlab/RAMDanceToolkit/tree/master/apps/RAMDanceToolkit/src/scenes/Notation)  example.

<br>

# ramGeometry

ramGeometry is used in the [Notation scene](), [Three Points scene]() and [Four Points scene]().
To use these methods, include _ramGeometry.h_ in the header file of your scene. 

#### void rotateToNormal(ofVec3f normal);

---

#### void approximatePlane(const vector<ofVec3f>& points, int iterations, ofVec3f& center, ofVec3f& normal);

---

#### ofVec2f closestPointOnRay(const ofVec2f& p1, const ofVec2f& p2, const ofVec2f& p3);

---

#### ofVec2f closestPointOnLine(const ofVec2f& p1, const ofVec2f& p2, const ofVec2f& p3);

---

#### ofVec2f closestPointOnRect(const cv::RotatedRect& rect, const ofVec2f& point);

---

#### ofVec2f closestPointOnCircle(const ofVec2f& center, float radius, const ofVec2f& point);

---

#### ofVec2f closestPointOnEllipse(const cv::RotatedRect& ellipse, const ofVec2f& point);

---

#### float distanceToEllipse(const ofVec2f& point, const cv::RotatedRect& ellipse);

---

#### float distanceToRect(const ofVec2f& point, const cv::RotatedRect& rect);

---

#### float distanceToRay(const ofVec2f& point, const ofVec2f& start, const ofVec2f& end);

---

#### float distanceToLine(const ofVec2f& point, const ofVec2f& start, const ofVec2f& end);

---

#### bool lineLineIntersectSegment(ofVec3f p1, ofVec3f p2, ofVec3f p3, ofVec3f p4, ofVec3f &pa, ofVec3f &pb);

---

#### ofVec3f lineLineIntersection(ofVec3f p1, ofVec3f p2, ofVec3f p3, ofVec3f p4);

---

#### void findCircle(const ofVec3f& a, const ofVec3f& b, const ofVec3f& c, ofVec3f& center, ofVec3f& normal, float& radius);

---

#### void findSphere(const ofVec3f& a, const ofVec3f& b, const ofVec3f& c, const ofVec3f& d, ofVec3f& center, float& radius);

---

<br>

	
# ramMovementAnalyser


<br>


# ramTimerdMovementAnalyser


<br>


# ramBalancer



<hr>
<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="http://i.creativecommons.org/l/by-sa/4.0/80x15.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">This Document</span> by <a xmlns:cc="http://creativecommons.org/ns#" href="http://interlab.ycam.jp/projects/ram" property="cc:attributionName" rel="cc:attributionURL">YCAM InterLab, Yoshito Onishi, Satoru Higa, Motoi Shimizu, and Kyle McDonald</a> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>.
