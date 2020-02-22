# hackhers20
2b915cf987e7eabb5e168fdefc5744f0cf028023b1c1c0545ff12655034dbc8a04422d806ee0a2ddbf7de14308134097130f691e797a0247f6e39b1a7cbb73a22
public static void main(String[] args) {
	
	String baseUrl = "https://hackicims.com:8080/api/v1/companies/2002";
	String auth = "Bearer $ab$a8$55b1efcf47a768ba4ae6eb7e3033a91f";

	//GET request to get company information
	HttpResponse companyResponse = get(baseUrl+"/", auth);

	//POST request to add a new job called HackHers
	String payload = "{\"title\":\"HackHers\"}";
	HttpResponse jobResponse = post(baseUrl+"/jobs", auth, payload);
}

public static HttpResponse get(String url, String auth) {
	
	try { 
		HttpClient client = HttpClientBuilder.create().build();
		HttpGet get = new HttpGet(url); //create GET request
		get.addHeader("Authorization", auth); //add authorization header
		get.addHeader("Content-Type", "application/json");
		
		HttpResponse response = client.execute(get); //execute the GET request
		return response;

	} catch(Exception e) {
		System.out.println("exception: " + e);
	}
	return null;
}

public static HttpResponse post(String url, String auth, String payload) {

	try{
		HttpClient client = HttpClientBuilder.create().build();     
		HttpPost post = new HttpPost(url); //create POST request
		post.addHeader("Authorization", auth); //add authorization header
		post.addHeader("Content-Type", "application/json");
		post.setEntity(new StringEntity(payload, ContentType.create("application/json"))); //add payload

		HttpResponse response = client.execute(post); //execute the POST request
		return response;

	} catch(Exception e) {
		System.out.println("exception: " + e);
	}
	return null;
}
