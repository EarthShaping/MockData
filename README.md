MockData
========

MockData is a random data generator.
Last release is a Beta Version 0.0.3

Let show you how use it.

Suppose you have a MOckObject :

public class MockPerson
{
   public int ID { get; set; }
   public String FirstName { get; set; }
   public String LastName { get; set; }
   public String Address { get; set; }
   public String City { get; set; }
   public String ZipCode { get; set; }
   public string Country { get; set; }
   public bool Status { get; set; }
   public string Details { get; set; }
}

You can write the following static helper :

public static class DummyData
{
    public static IList<mockperson> GetDataPerson(int number)
    {
        return Enumerable.Range(0,number).Select(o =>  new MockPerson
	      {
	        FirstName = MockData.Person.FirstName(),
	        ID = MockData.RandomNumber.Next(0,number*100),				
          	LastName = MockData.Person.Surname(),
	        Address = MockData.Address.StreetAddress(),
	        City = MockData.Address.City(),
	        ZipCode = MockData.Address.ZipCode(),
	        Country = MockData.Address.DefaultCountry(),
	        Status = new Random().Next(0, 2) == 1 ? true : false,
	        Details = MockData.Lorem.Paragraph(1)
	      }).ToList();
	      }
    }
}

After you can call :

 List<MockPerson> list = DummyData.GetDataPerson(300);
 
that return a list with 300 records of the type MockPerson.


