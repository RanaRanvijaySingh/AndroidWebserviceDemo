AndroidWebserviceDemo
=====================

This project demonstrate how to use the webservice in your project.Accessing the web service is very simple thing.All you need to do is to use few objects to initialize and send request , like HttpGet , HttpRequest , HttpResponse.

----------------------------------------------------------------------------------------------------------------------------

	HttpClient client = new DefaultHttpClient();
	HttpGet get = new HttpGet("http://api.androidhive.info/contacts/");
	HttpResponse response = client.execute(get);
	StatusLine statusLine = response.getStatusLine();
	int statusCode = statusLine.getStatusCode();
	HttpEntity entity = response.getEntity();

----------------------------------------------------------------------------------------------------------------------------

	Step 1: Give the permission in the manifest file .
	Step 2: Create a simple Textview in the layout.
	Step 3: Create the main Class to use the objects.

____________________________________________________________________________________________________________________________________________________________
####Step 1: Give the permission in the manifest file .
=======
Step 1: Give the permission in the manifest file .
Step 2: Create a simple Textview in the layout.
Step 3: Create the main Class to use the objects.

____________________________________________________________________________________________________________________________________________________________
Step 1: Give the permission in the manifest file .

     <uses-permission android:name="android.permission.INTERNET"/>
     <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
____________________________________________________________________________________________________________________________________________________________

####Step 2: Create a simple Textview in the layout.
=======
Step 2: Create a simple Textview in the layout.

    <TextView
        android:id="@+id/textViewResponse"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:text="@string/hello_world" />
____________________________________________________________________________________________________________________________________________________________

####Step 3: Create the main Class to use the objects.

		String readTwitterFeed = readTwitterFeed();
	
		private String readTwitterFeed() {
=======
Step 3: Create the main Class to use the objects.

		String readTwitterFeed = readTwitterFeed();
	
		private String readTwitterFeed() {
		StringBuilder sBuilder = new StringBuilder();
		HttpClient client = new DefaultHttpClient();
		HttpGet get = new HttpGet("http://api.androidhive.info/contacts/");
		try {
			HttpResponse response = client.execute(get);
			StatusLine statusLine = response.getStatusLine();
			int statusCode = statusLine.getStatusCode();
			if (statusCode == 200) {
				HttpEntity entity = response.getEntity();
				InputStream content = entity.getContent();
				BufferedReader reader = new BufferedReader(
						new InputStreamReader(content));
				String line;
				while ((line = reader.readLine()) != null)
					sBuilder.append(line);
			}
		} catch (IOException e) {
			e.printStackTrace();
		}
		return sBuilder.toString();
	}
