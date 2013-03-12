# Recognizer


### Summary

This page shows some preset recognizers.

### table of contents

- [Introduction to ramBaseRecognizer](Introduction to ramBaseRecognizer)
- [ramGeometry](ramGeometry)
- [ramMovementAnalyser](ramMovementAnalyser)
- [ramTimerdMovementAnalyser](ramTimerdMovementAnalyser)
- [ramBalancer](ramBalancer)


# Introduction to ramBaseRecognizer

In RAMDanceToolkit 1.0.0, ramRecognizer is an experimental class.
There are many case of analysis result which will be returned so currently this class doesn't have regular format. Please post an issue or send pull request if you have an ideas concerning this class. 

Current ramBaseRecognizer is empty:

	class ramBaseRecognizer : public ramUnit {
	public:
	};

See also [Notation scene]() as recognizer example.

<br>

# ramGeometry

ramGeometry is used in [Notation scene](), [Three Points scene](), [Four Points scene]() .
To use these methods, include _ramGeometry.h_ to header file of your scene. 

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