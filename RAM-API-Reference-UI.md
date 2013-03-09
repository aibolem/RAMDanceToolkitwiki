
# UI

# ramControlPanel


	void save(const string& path);
	void load(const string& path);
	
	
	void addPanel(ofxUITab& tab);
	void addSection(const string& name);
	void addSeparator();
	void addLabel(const string& content);
	ofEvent<ofEventArgs>& addButton(const string& name);
	void addToggle(const string& name, bool *value);
	void addMultiToggle(const string& name, const vector<string>& content, int *value);
	ofxUIRadio* addRadioGroup(const string& name, const vector<string>& content, int *value);
	void addDropdown(const string& name, const vector<string>& content, int *value);
	void addSlider(const string& name, float min_value, float max_value, float *value);
	void addColorSelector(const string& name, ofFloatColor *value);


