
# Utility


## ramNodeFinder


--

#### bool ramNodeFinder::findOne(ramNode &node)

text

--

#### vector<ramNode> findAll()

text

--


## ramNodeIdentifer

	ramNodeIdentifer() : name(""), index(-1) {}
	ramNodeIdentifer(int index) : name(""), index(index) {}
	ramNodeIdentifer(const string &name) : name(name), index(-1) {}
	ramNodeIdentifer(const string &name, int index) : name(name), index(index) {}
	ramNodeIdentifer(const ramNodeIdentifer& copy) { *this = copy; }


## ramCameraSettings

## ramTSVCoder

## ramNodeArrayBuffer

## ramCompoundContainer

## ramFading