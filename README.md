import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.net.HttpURLConnection;
import java.net.URL;

public class Test {

	public static void main(String[] args) throws Exception {
		URL url = new URL(
				"https://raw.githubusercontent.com/llm1993/test/master/README.md");
		HttpURLConnection httpURLConnection = (HttpURLConnection) url
				.openConnection();
		httpURLConnection.setRequestMethod("GET");
		BufferedReader bufferedReader = new BufferedReader(
				new InputStreamReader(httpURLConnection.getInputStream()));
		String lineString = null;
		boolean flag = true;
		StringBuilder stringBuilder = new StringBuilder();
		while ((lineString = bufferedReader.readLine()) != null && flag) {
			System.out.println(lineString+"123132131");
			stringBuilder.append(lineString+"\r\n");
		}
	}







}
