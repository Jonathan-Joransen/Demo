# Demo

I had an issue with connections not getting terminated correctly.
This code is not only fun becuase I like being able to use interesting patterns,
but it was extremely practical to use the pattern in this situation. 

`
  useConnection = async (
    callback: (conn: PoolConnection) => Promise<any>
  ): Promise<any> => {
    let currConn = await this.conn.getConnection();
    let result: any;
    try {
      result = await callback(currConn);
    } finally {
      currConn.release();
    }
    return result;
  };
`
