# Post-Office
CS2 assignment (Dalton)
import java.util.Scanner;
public class Post_Office {

	/**
	 * Author: Raina Lopez
	 * Errors:
	 * Changes: finished mail sorting, finished zip to zone conversion
	 * Stuff I have to do: add the prices of stuff and do the zone math
	 * Notes: all prices in the code are in cents
	 */
	public static void main(String[] args) {
		// TODO Auto-generated method stub

		//int[] PostOffice = new int[] 
		//	{1,2,3};
		Scanner scanA = new Scanner(System.in);	//user
		Scanner scanB = new Scanner(System.in);
		Scanner scanC = new Scanner(System.in);
		Scanner scanD = new Scanner(System.in);
		Scanner scanE = new Scanner(System.in);

		double length = scanA.nextDouble();
		double height = scanB.nextDouble();
		double thickness = scanC.nextDouble();

		int zip1 = scanD.nextInt();
		int zip2 = scanE.nextInt();
		int ZoneA = 0;
		int ZoneB = 0;
		int ZoneDist = 0;

		int baseprice = 0;
		int finalprice = 0;

		String mailType = "";

		int loop = 0;
		boolean mailable = true;


		//length width and thickness to string
		if((length >= 3.5 && length <= 4.25) && (height >= 3.5 && height <= 6) && (thickness >= .007 && thickness <= .016))
		{
			mailType = "REGULAR POST CARD";
			baseprice = 20;
		}
		else if((length > 4.25 && length < 6) && (height > 6 && height < 11.5) && (thickness >= .007 && thickness <= .015))
		{
			mailType = "LARGE POST CARD";
			baseprice = 37;
		}
		else if((length >= 3.5 && length <= 6.125) && (height >= 5 && height <= 11.5) && (thickness > .016 && thickness < .25))
		{
			mailType = "ENVELOPE";
			baseprice = 37;
		}
		else if((length > 6.125 && length < 24) && (height >= 11 && height <= 18) && (thickness >= .25 && thickness <= .5))
		{
			mailType = "LARGE ENVELOPE";
			baseprice = 60;
		}
		else if(length > 24 || height > 18 || thickness > .5 && (length + (2*height + 2*thickness) <= 84))
		{
			mailType = "PACKAGE";
			baseprice = 295;
		}
		else if(length + (2*height + 2*thickness) > 84 && length + (2*height + 2*thickness) <= 130)
		{
			mailType = "LARGE PACKAGE";
			baseprice = 395;
		}
		else
		{
			mailType = "UNMAILABLE";
		}


		//zip code to zone sorter
		if (zip1 <= 6999)
		{
			ZoneA = 1;
		}
		else if (zip1 > 6999 && zip1 <= 19999 )
		{
			ZoneA = 2;
		}
		else if (zip1 > 19999 && zip1 <= 35999 )
		{
			ZoneA = 3;
		}
		else if (zip1 > 35999 && zip1 <= 62999 )
		{
			ZoneA = 4;
		}
		else if (zip1 > 62999 && zip1 <= 84999 )
		{
			ZoneA = 5;
		}
		else if (zip1 > 84999 && zip1 <= 99999 )
		{
			ZoneA = 6;
		}
		else 
		{
			mailType = "UNMAILABLE";
		}

		//System.out.println("zip2: "+zip2);
		//zip2 to zone sorter
		if (zip2 <= 6999)
		{
			ZoneB = 1;
		}
		else if (zip2 > 6999 && zip2 <= 19999 )
		{
			ZoneB = 2;
		}
		else if (zip2 > 19999 && zip2 <= 35999 )
		{
			ZoneB = 3;
		}
		else if (zip2 > 35999 && zip2 <= 62999 )
		{
			ZoneB = 4;
		}
		else if (zip2 > 62999 && zip2 <= 84999 )
		{
			ZoneB = 5;
		}
		else if (zip2 > 84999 && zip2 <= 99999 )
		{
			ZoneB = 6;
		}
		else 
		{
			mailType = "UNMAILABLE";
		}

		ZoneDist = ZoneA-ZoneB;
		ZoneDist = (Math.abs(ZoneDist));

		if (mailType.equals("UNMAILABLE"))
		{
			System.out.println("UNMAILABLE");
		}

		else
		{
			if (mailType.equals("REGULAR POST CARD"))
			{
				finalprice = baseprice + 3 * ZoneDist;
			}
			else if (mailType.equals("LARGE POST CARD"))
			{
				finalprice = baseprice + 3 * ZoneDist;
			}
			else if (mailType.equals("ENVELOPE"))
			{
				finalprice = baseprice + 4 * ZoneDist;
			}
			else if (mailType.equals("LARGE ENVELOPE"))
			{
				finalprice = baseprice + 5 * ZoneDist;
			}
			else if (mailType.equals("PACKAGE"))
			{
				finalprice = baseprice + 25 * ZoneDist;
			}
			else if (mailType.equals("LARGE PACKAGE"))
			{
				finalprice = baseprice + 35 * ZoneDist;
			}

			System.out.println(finalprice + "¢");
		} 

	}
	//code

}
