class BIOSUiSetupElement(object):
    def get_processors_l2_cache_ram(self, timeout=20):
        """*Advanced -> Processor Configuration -> L2 Cache RAM*

        get processors L2 cache ram value in KB, When the CPU is not installed,
        the obtained l2 cache is "N/A" and return None

        :param timeout: End the program after the specified seconds have elapsed
        :return: processors L2 cache ram value in KB in list
        """

    def get_total_processor_cores(self, timeout=20):
        """*Advanced -> Processor Configuration -> Total Processor Cores*

        get total processor cores

        :param timeout: End the program after the specified seconds have elapsed
        :return: the number of cores in the processor package
        """

    def get_current_tpm_device(self, timeout=20):
        """*Security -> Current TPM Device*

        get current TPM device, this item will not be able to get and return
        timeout if TPM device is not active

        :param timeout: End the program after the specified seconds have elapsed
        :return: current TPM device or None
        """

    def get_memory_encryption(self, timeout=20):
        """*Advanced -> Processor Configuration -> Memory Encryption (TME)*

        get the TME setting

        :param timeout: End the program after the specified seconds have elapsed
        :return: the TME setting
        """

    def set_memory_encryption(self, value, timeout=20):
        """*Advanced -> Processor Configuration -> Memory Encryption (TME)*

        changing the TME setting

        :param value: the value that would perform. Currently would support list is:
            Disabled, Enabled, defaults to Disabled
        :param timeout: End the program after the specified seconds have elapsed
        :return: Execution completion code.
        """

    def get_intel_txt(self, timeout=20):
        """*Advanced -> Processor Configuration -> Intel(R) TXT*

        get the Intel TXT setting

        :param timeout: End the program after the specified seconds have elapsed
        :return: Intel TXT setting
        """

    def set_intel_txt(self, value, timeout=20):
        """*Advanced -> Processor Configuration -> Intel(R) TXT*

        changing the Intel TXT setting, the TPM must be active, otherwise the item
        will be gray out. It requires the system to perform a hard reset for the
        setting to become effective

        :param value: the value that would perform. Currently would support list is:
            Disabled, Enabled, defaults to Disabled
        :param timeout: End the program after the specified seconds have elapsed
        :return: Execution completion code.
        """

    def get_intel_vt_for_directed(self, timeout=20):
        """*Advanced -> Integrated IO configuration -> Intel(R) VT for Directed I/O*

        get Intel(R) VT for Directed I/O setting

        :param timeout: End the program after the specified seconds have elapsed
        :return: the Intel(R) VT for Directed setting
        """

    def set_intel_vt_for_directed(self, value, timeout=20):
        """*Advanced -> Integrated IO configuration -> Intel(R) VT for Directed I/O*

        changing the Intel(R) VT for Directed I/O setting, when changing Intel VT
        from Enabled to Disabled, first make sure Intel TXT is set to Disabled

        :param value: the value that would perform. Currently would
            support list is: Disabled, Enabled, defaults to Disabled
        :param timeout: End the program after the specified seconds have elapsed
        :return: Execution completion code
        """ 
		
	def get_processors_l3_cache_ram(self, timeout=20):
		"""*Advanced>processor configuration >l3 cache*
		
		get processors L3 cache ram value in KB
		
		:param timeout: End the program after the specified seconds have elapsed
		:return: processors L1 cache ram value in KB in list
		"""
		pass


	def get_key_stock_amount(self, timeout=20):
		"""*Advanced>processor configuration >Key stock amount*
		
		Check the status of TME and get the value of key_stock_amount.
			If TME is not enable, return -1,else get key stock amount,
			value range in [0 - (2^TME-MT key ID bits - 1)]
			
		:param timeout: End the program after the specified seconds have elapsed
		:return: The value of key stock amount
		"""
		pass


	def get_tme_mt_key_id(self, timeout=20):
		"""*Advanced>processor configuration >TME-MT key ID bits*
		
		Check the status of TME and get the value of TME-MT key id bits.
			If TME is not enable, return -1,else get the value of TME-MT key ID bits,
			value range in [0-15].
			
		:param timeout: End the program after the specified seconds have elapsed
		:return: the value of TME-MT key ID bits
		"""
		pass



	def get_intel_virtualization_technology(self, timeout=20):
		"""*Advanced>processor configuration> Intel virtualization technology*
		
		Get the status of Intel(R) virtualization technology,
			value range in ['enable','disable'].
			
		:param timeout: End the program after the specified seconds have elapsed
		:return: the status of Intel(R) virtualization technology
		"""
		pass


	def set_intel_virtualization_technology(self, option, timeout=20):
		"""*Advanced>processor configuration> Intel virtualization technology*
		
		Set the status of Intel(R) virtualization technology
		
		:param timeout: End the program after the specified seconds have elapsed
		:param option: The option need to be set.It is only acceptable as a str in list ['enable','disable'],
			or it will raise a TypeError Exception.
		:return: the status of Intel(R) virtualization technology
		"""
		pass



	def get_volatile_memory_mode(self, timeout=20):
		"""*Advanced>memory configuration>volatile memory mode*
		
		Get the value of volatile_memory_mode,
			value range in ['1LM','2LM','1LM+2LM'].
			
		:param timeout: End the program after the specified seconds have elapsed
		:return: the value of volatile_memory_mode
		"""
		pass


	def set_volatile_momery_mode(self, option, timeout=20):
		"""*Advanced>memory configuration>volatile memory mode*
		
		Set the status of Volatile Memory Mode
		
		:param timeout: End the program after the specified seconds have elapsed
		:param option: The option need to be set.It is only acceptable as a str in list ['1LM','2LM','1LM+2LM'],or it will raise a TypeError Exception.
		:return: the status of Volatile Memory Mode
		"""
		pass