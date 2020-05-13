using System;
using System.Collections.Generic;
using System.Linq;
using SharpSploit.Enumeration;
using SharpSploit.Execution;

    public static class Task
    {
        public static string Execute()
        {
            try 
			{
				var scHandle = IntPtr.Zero;
				Domain.DomainSearcher searcher = new Domain.DomainSearcher();
				List<Domain.DomainObject> computerList = searcher.GetDomainComputers();
				List<string> adminFound = new List<string>();
				foreach (Domain.DomainObject computer in computerList)
				{
					string computerName = computer.name;

					scHandle = Win32.Advapi32.OpenSCManager(computerName, null, Win32.Advapi32.SCM_ACCESS.SC_MANAGER_ALL_ACCESS);

					if (scHandle.ToInt32() != 0)
					{
						adminFound.Add(computer.distinguishedname);

					}
					Win32.Advapi32.CloseServiceHandle(scHandle);
				}
                if(adminFound.Count() == 0)
                {
                	return "No admin access found.";
                }
				else{
                	string result = string.Join(",", adminFound.ToArray());
					return result;
                }
			}
            catch (Exception e) {return e.GetType().FullName + ": " + e.Message + Environment.NewLine + e.StackTrace;}
        }
    }
