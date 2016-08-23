import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.net.HttpURLConnection;
import java.net.URL;

public class Test {

	public static void main(String[] args) throws Exception {
		URL url = new URL(
				"https://github.com/llm1993/test/blob/master/README.md");
		HttpURLConnection httpURLConnection = (HttpURLConnection) url
				.openConnection();
		httpURLConnection.setRequestMethod("GET");
		BufferedReader bufferedReader = new BufferedReader(
				new InputStreamReader(httpURLConnection.getInputStream()));
		String lineString = null;
		boolean flag = true;
		StringBuilder stringBuilder = new StringBuilder();
		while ((lineString = bufferedReader.readLine()) != null && flag) {
			if (lineString.contains("<article")) {
				stringBuilder.append(lineString.substring(lineString
						.indexOf("<p>") + 3) + "\r\n");
				while ((lineString = bufferedReader.readLine()) != null) {
					if (lineString.contains("&lt;"))
						lineString = lineString.replaceAll("&lt;", "<");
					if (lineString.contains("</article>")) {
						flag = false;
						stringBuilder.delete(stringBuilder.lastIndexOf("</p>"),
								stringBuilder.lastIndexOf("</p>") + 4);
						break;
					}
					stringBuilder.append(lineString + "\r\n");
				}
			}
		}
		System.out.println(stringBuilder);
	}

}
